# Integração CRM GLIX × ERP Sankhya

Documentação técnica para integração do CRM GLIX com o ERP Sankhya via API REST.

---

## Visão geral

O Sankhya disponibiliza uma API REST (MGE) que permite consultar e manipular dados do ERP. A integração com o CRM GLIX ocorrerá nos seguintes fluxos:

```
CRM GLIX  ←→  API Sankhya (MGE)
   │                  │
   ├── Contatos   ←── Parceiros (TGFPAR)
   ├── Empresas   ←── Parceiros PJ (TGFPAR)
   ├── Negócios   ──► Pedidos (TGFCAB / TGFITE)
   └── Status     ←── Notas Fiscais (webhook)
```

---

## Autenticação Sankhya

```javascript
// POST /mge/service.sbr?serviceName=MobileLoginSP.login
const login = await fetch(`${SANKHYA_URL}/mge/service.sbr?serviceName=MobileLoginSP.login`, {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    serviceName: 'MobileLoginSP.login',
    requestBody: {
      NOMUSU: { $: 'usuario' },
      INTERNO: { $: 'senha' },
      KEEPCONNECTED: { $: 'S' }
    }
  })
});
const { bearerToken } = await login.json();
```

---

## Endpoints principais

### Listar parceiros (clientes)
```javascript
// GET parceiros para importar como contatos
GET /mge/service.sbr?serviceName=DbExplorerSP.loadRecords
Body: {
  "serviceName": "DbExplorerSP.loadRecords",
  "requestBody": {
    "dataSet": {
      "rootEntity": "Parceiro",
      "includePresentationFields": "S",
      "offsetPage": "0",
      "criteria": {
        "expression": { "$": "this.ATIVO = 'S'" }
      },
      "entity": {
        "fieldset": {
          "list": "CODPARC,NOMEPARC,EMAIL,TELEFONE,CGC_CPF,TIPOPESSOA"
        }
      }
    }
  }
}
```

### Criar pedido ao fechar negócio
```javascript
// POST pedido de venda no Sankhya
POST /mge/service.sbr?serviceName=CACSP.incluirCabecalho
Body: {
  "serviceName": "CACSP.incluirCabecalho",
  "requestBody": {
    "cabecalho": {
      "CODPARC":   { "$": codparcSankhya },
      "DTNEG":     { "$": dataFechamento },
      "CODTIPOPER": { "$": "1001" },  // tipo de operação de venda
      "CODVEND":   { "$": codVendedor }
    }
  }
}
```

---

## Mapeamento de campos

| CRM GLIX | Tabela Sankhya | Campo Sankhya |
|---|---|---|
| `contato.name` | TGFPAR | NOMEPARC |
| `contato.email` | TGFPAR | EMAIL |
| `contato.phone` | TGFPAR | TELEFONE |
| `empresa.cnpj` | TGFPAR | CGC_CPF |
| `negocio.value` | TGFCAB | VLRNOTA |
| `negocio.closeDate` | TGFCAB | DTNEG |
| `negocio.owner` | TGFCAB | CODVEND |

---

## Configuração no CRM GLIX

Na tela `Configurações > Integração Sankhya`, preencha:

| Campo | Exemplo |
|---|---|
| URL do servidor | `https://sankhya.suaempresa.com.br` |
| Token / Usuário | gerado em Sankhya > Configurações > API |
| Sincronizar clientes | ✅ Ativado |
| Sincronizar pedidos | ✅ Ativado |
| Webhook NF | Configurar URL em Sankhya > Eventos |

---

## Webhook — Nota Fiscal emitida

Quando o Sankhya emitir uma NF, ele chamará o endpoint do CRM:

```
POST https://crm.glix.com.br/webhook/sankhya/nf-emitida
Headers: X-Sankhya-Token: <token>
Body: {
  "NUNOTA": 12345,
  "CODPARC": 678,
  "VLRNOTA": 45000.00,
  "DTNEG": "2025-05-06"
}
```

O CRM então atualiza o negócio relacionado para status **"NF Emitida"**.

---

## Referências

- [Documentação oficial Sankhya API](https://developer.sankhya.com.br)
- [Portal do Parceiro Sankhya](https://parceiro.sankhya.com.br)
- [Fórum Sankhya Developers](https://community.sankhya.com.br)
