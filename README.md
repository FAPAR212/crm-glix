# CRM - GLIX

> Sistema de Gestão de Relacionamento com o Cliente — preparado para integração com **ERP Sankhya**

![Versão](https://img.shields.io/badge/versão-1.0.0-blue)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Licença](https://img.shields.io/badge/licença-MIT-green)

---

## 📋 Sobre o projeto

O **CRM GLIX** é um sistema completo de gestão de relacionamento com clientes, desenvolvido para operar de forma standalone e, futuramente, integrado ao **ERP Sankhya** via API REST.

---

## 🚀 Funcionalidades

| Módulo | Descrição | Status |
|---|---|---|
| Dashboard | KPIs, funil de vendas, ranking de vendedores | ✅ Pronto |
| Pipeline | Kanban com drag & drop entre estágios | ✅ Pronto |
| Contatos | CRUD completo com filtros | ✅ Pronto |
| Empresas | Cards com métricas por empresa | ✅ Pronto |
| Atividades | Checklist com prioridades e prazos | ✅ Pronto |
| Relatórios | Gráficos de receita, origem e ticket médio | ✅ Pronto |
| Configurações | Painel de integração Sankhya | ✅ Pronto |
| **Integração Sankhya** | Sync de parceiros, pedidos e NF | 🔜 Próxima versão |

---

## 🏗️ Estrutura do projeto

```
crm-glix/
├── src/
│   └── index.html          # Aplicação principal (HTML + CSS + JS inline)
├── assets/
│   └── (imagens, ícones futuros)
├── docs/
│   ├── INTEGRACAO_SANKHYA.md
│   └── ROADMAP.md
├── README.md
├── CHANGELOG.md
└── .gitignore
```

---

## ⚡ Como usar

1. Clone o repositório:
```bash
git clone https://github.com/SEU_USUARIO/crm-glix.git
```

2. Abra o arquivo no navegador:
```bash
cd crm-glix
open src/index.html
# ou arraste o arquivo para o Chrome/Edge
```

> Nenhuma dependência ou instalação necessária. Funciona 100% no navegador.

---

## 🔗 Integração Sankhya (em desenvolvimento)

A integração com o ERP Sankhya será feita via **API REST**. Configure em `Configurações > Integração Sankhya`:

- **URL do servidor**: endpoint da API Sankhya
- **Token**: chave de parceiro Sankhya
- **Sincronizações disponíveis**:
  - Parceiros (clientes/fornecedores) → Contatos
  - Pedidos → Negócios fechados
  - Notas fiscais → Webhook de atualização de status

Consulte [docs/INTEGRACAO_SANKHYA.md](docs/INTEGRACAO_SANKHYA.md) para detalhes técnicos.

---

## 📅 Roadmap

Veja [docs/ROADMAP.md](docs/ROADMAP.md) para o plano de desenvolvimento.

---

## 📝 Changelog

Veja [CHANGELOG.md](CHANGELOG.md) para histórico de versões.

---

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch: `git checkout -b feature/nova-funcionalidade`
3. Commit suas mudanças: `git commit -m 'feat: adiciona nova funcionalidade'`
4. Push para a branch: `git push origin feature/nova-funcionalidade`
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para detalhes.

---

**Desenvolvido por GLIX** • Integração Sankhya em breve 🚀
