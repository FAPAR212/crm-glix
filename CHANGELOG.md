# Changelog — CRM GLIX

Todas as mudanças notáveis neste projeto serão documentadas aqui.

Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto segue o [Versionamento Semântico](https://semver.org/lang/pt-BR/).

---

## [1.0.0] — 2025-05-06

### Adicionado
- **Dashboard** com KPIs em tempo real (receita, leads, negócios, conversão)
- **Funil de vendas** visual com 5 estágios
- **Ranking de vendedores** com barras de progresso
- **Feed de atividades pendentes** no dashboard
- **Pipeline Kanban** com drag & drop entre colunas
- **Módulo de Contatos** com CRUD completo
  - Criação, edição e exclusão de contatos
  - Filtros por status e vendedor responsável
- **Módulo de Empresas** com cards e métricas
- **Módulo de Atividades** com checklist, prioridades e prazos
  - Marcar como concluída
  - Filtros por status (todas / pendentes / concluídas)
- **Módulo de Relatórios**
  - Gráfico de barras — receita mensal
  - Gráfico donut — origem de leads
  - Ticket médio por segmento
  - Tempo médio de fechamento
- **Painel de Configurações** com seção dedicada à integração Sankhya
  - Campo de URL do servidor Sankhya
  - Token de autenticação
  - Toggles de sincronização (parceiros, pedidos, NF)
  - Seletor de intervalo de sincronização automática
- **Sistema de notificações** (toast) para feedback de ações
- **Busca global** na topbar
- **Modal reutilizável** para criação de contatos, negócios, atividades e empresas
- Design dark mode com paleta profissional
- Totalmente responsivo e sem dependências externas

### Técnico
- Aplicação single-file HTML (CSS + JS inline)
- Zero dependências — funciona diretamente no navegador
- Estado gerenciado em memória via objeto JS
- Estrutura preparada para futura modularização

---

## [Próximas versões]

### [1.1.0] — Planejado
- Integração real com API REST Sankhya
- Sincronização de parceiros Sankhya → Contatos CRM
- Criação automática de pedidos Sankhya ao fechar negócio

### [1.2.0] — Planejado
- Persistência de dados (localStorage / backend)
- Sistema de autenticação de usuários
- Perfis e permissões por usuário

### [1.3.0] — Planejado
- Importação de contatos via CSV
- Exportação de relatórios em PDF/Excel
- Integração com e-mail (envio direto pelo CRM)

### [2.0.0] — Visão futura
- Backend Node.js / API REST própria
- Banco de dados PostgreSQL
- App mobile (React Native)
- Webhooks Sankhya bidirecional
