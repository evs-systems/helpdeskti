# 🖥️ HelpDesk TI

Sistema completo de **Gestão de Chamados, Inventário e Organização** para equipes de Tecnologia da Informação. Desenvolvido como uma aplicação web single-page (SPA) com React e Firebase, hospedado gratuitamente no GitHub Pages.

---

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias](#-tecnologias)
- [Arquitetura](#-arquitetura)
- [Configuração do Firebase](#-configuração-do-firebase)
- [Implantação](#-implantação)
- [Perfis de Acesso](#-perfis-de-acesso)
- [Segurança](#-segurança)

---

## 🎯 Visão Geral

O HelpDesk TI é uma plataforma projetada para centralizar e otimizar a operação de equipes de suporte técnico em ambientes corporativos com múltiplas unidades. Ele permite que **colaboradores** abram chamados e acompanhem o andamento em tempo real, enquanto **técnicos de TI** gerenciam todo o ciclo de vida do atendimento, inventário de equipamentos e tarefas internas — tudo em uma única interface.

A aplicação funciona inteiramente no navegador, sem necessidade de backend próprio, utilizando o **Firebase** como infraestrutura de dados em tempo real.

---

## ✨ Funcionalidades

### 📩 Gestão de Chamados
- Abertura de chamados por **Problema Técnico** ou **Solicitação**.
- Fluxo completo de status: `Aguardando` → `Em Atendimento` → `Aguardando Autorização` → `Finalizado`.
- Sistema de **contestação**: colaboradores podem reabrir chamados finalizados.
- Atribuição de **prioridade** (Baixa, Média, Alta) e **técnico responsável**.
- Filtros por unidade, prioridade, tipo e busca textual.
- Visualização separada: chamados ativos, de outros técnicos, contestados e arquivados.
- Histórico completo de alterações por chamado.

### 💬 Chat em Tempo Real
- **Chat público** em cada chamado para comunicação direta entre colaborador e técnico.
- **Chat interno** (visível apenas para técnicos) para alinhamento da equipe sobre um chamado.
- Envio de **imagens** via upload ou `Ctrl+V` (colar da área de transferência).
- Visualizador de imagens integrado com zoom e navegação em galeria.
- Indicadores de mensagens não lidas com notificações sonoras e visuais.

### 🌐 Chat Global (Suporte Rápido)
- Canal de comunicação direta entre **setores/unidades** e a equipe de TI.
- **Chat interno exclusivo** entre técnicos para discussões privadas.
- Sistema de salas automáticas organizadas por Unidade + Setor.
- Respostas com citação (reply), edição de mensagens e separador de datas.
- Notificações no navegador (push) e toasts interativos com ação "Ver Chat".

### 📊 Relatórios e Dashboards
- Gráficos interativos de **volume de chamados** (por hora, dia ou mês) com Chart.js.
- Gráfico de rosca com distribuição entre **Problemas Técnicos** e **Solicitações**.
- Filtros por período: Hoje, Mês atual, Ano completo ou período personalizado.
- Estatísticas detalhadas: total, finalizados, contestados, unidade/setor com mais demanda.
- Ranking de desempenho por técnico (chamados ativos vs. finalizados).

### 🗄️ Inventário de Equipamentos
- Cadastro completo: modelo, tipo, nº de série, ID do dispositivo, IP, AnyDesk, especificações, preço, datas de aquisição e garantia.
- Controle de status: **Em Uso** ou **Guardado**.
- Sistema de **baixa** com registro de motivo e possibilidade de restauração.
- Filtros por tipo de equipamento, unidade e status.
- **Importação em massa** via arquivo CSV com modelo de planilha para download.
- **Exportação** da lista filtrada para CSV.
- Histórico de movimentações por equipamento.

### 🧮 Controle de Acessórios
- Cadastro de acessórios (Mouse, Teclado, Fones, Cabos, etc.) com controle de estoque.
- **Movimentações**: entrada e saída de itens com registro de destino (unidade/setor).
- Visualização de movimentações por mês/ano com filtro por tipo de acessório.
- Agrupamento por item com resumo de entradas e saídas.

### 📌 Quadro Kanban (Organização TI)
- Quadro de tarefas com colunas: **A Fazer**, **Em Andamento**, **Em Revisão** e **Concluído**.
- **Arrastar e soltar** (drag-and-drop) entre colunas.
- Detalhes com descrição, responsável, anexos e comentários.
- Upload de documentos e arquivos de apoio por tarefa.

### 📚 Base de Conhecimento
- Registro de **informações padrão** da equipe (senhas, procedimentos, links úteis).
- Busca por título ou conteúdo.
- Suporte a anexos: documentos, imagens e arquivos auxiliares.

### ✅ Checklist de Tarefas Recorrentes
- Tarefas com recorrência **diária**, **semanal** ou **mensal**.
- Controle automático de pendências (a tarefa reaparece quando vence o ciclo).
- Histórico de conclusão com responsável e data.
- Atribuição de responsável opcional.

### 📢 Avisos Globais
- Publicação de avisos visíveis para **todos os usuários** do sistema.
- Três níveis: **Informativo**, **Atenção** e **Crítico**.
- Notificações sonoras e push ao publicar novos avisos.
- Banner fixo no topo do dashboard com destaque visual por prioridade.

### 🌙 Interface
- **Tema Claro e Escuro** com sincronização nativa (inclusive para Safari/iOS).
- Design responsivo e mobile-first com menu lateral adaptativo.
- **PWA** (Progressive Web App): instalável como aplicativo no desktop e celular.
- Notificações nativas do sistema operacional (browser push notifications).
- Controle de áudio (ativar/desativar sons de notificação).
- Frases motivacionais diárias no dashboard do técnico.

---

## 🛠️ Tecnologias

| Camada | Tecnologia | Uso |
|--------|-----------|-----|
| **UI Framework** | React 18 (via ESM CDN) | Componentes e estado |
| **Estilização** | TailwindCSS (CDN) | Classes utilitárias e responsividade |
| **Ícones** | Lucide React | Iconografia consistente |
| **Gráficos** | Chart.js | Relatórios visuais |
| **Transpilação** | Babel Standalone | JSX no navegador |
| **Backend** | Firebase | Auth, Firestore, Storage |
| **Hospedagem** | GitHub Pages | Deployment estático |
| **PWA** | Service Worker + Manifest | Instalação como app |

> **Nota:** A aplicação é um arquivo HTML único (`index.html`) que carrega todas as dependências via CDN, sem necessidade de build, bundler ou servidor Node.js.

---

## 🏗️ Arquitetura

```
index.html (Single-File Application)
│
├── <head>
│   ├── PWA Manifest (gerado em runtime via JS)
│   ├── Service Worker (inline blob)
│   ├── TailwindCSS (CDN)
│   ├── Chart.js (CDN)
│   ├── Import Map (React, Firebase, Lucide)
│   └── Babel Standalone
│
└── <body>
    └── <script type="text/babel">
        ├── Firebase Init (Auth, Firestore, Storage)
        ├── Funções utilitárias (formatação, normalização)
        ├── Componente ImageViewer
        └── Componente App (principal)
            ├── Estado global (useState/useEffect)
            ├── Listeners em tempo real (onSnapshot)
            ├── Handlers de CRUD
            └── Renderização condicional por view
```

### Coleções do Firestore

| Coleção | Descrição |
|---------|-----------|
| `chamados` | Chamados de suporte com mensagens e histórico |
| `global_chats` | Salas de chat global por setor/unidade + chat interno TI |
| `equipamentos` | Inventário de equipamentos com histórico de movimentação |
| `acessorios` | Controle de estoque de acessórios |
| `kanban_cards` | Tarefas do quadro Kanban |
| `kb_cards` | Informações padronizadas da base de conhecimento |
| `checklists` | Tarefas recorrentes com histórico de conclusão |
| `avisos` | Avisos globais do sistema |

### Buckets do Storage

| Caminho | Uso | Acesso |
|---------|-----|--------|
| `attachments/{ticketId}/` | Imagens do chat de chamados | Todos (somente imagens, máx 5MB) |
| `global_chat/{chatId}/` | Imagens do chat global | Todos (somente imagens, máx 5MB) |
| `kanban_cards_attachments/{cardId}/` | Anexos das tarefas Kanban | Somente técnicos (máx 10MB) |
| `kb_cards_attachments/{cardId}/` | Anexos da base de conhecimento | Somente técnicos (máx 10MB) |

---

## 🔥 Configuração do Firebase

### 1. Criar Projeto

1. Acesse o [Firebase Console](https://console.firebase.google.com/).
2. Crie um novo projeto (ou use um existente).
3. Registre um app Web e copie o objeto `firebaseConfig`.

### 2. Atualizar Configuração

No arquivo `index.html`, localize e substitua o bloco `firebaseConfig` com as credenciais do seu projeto:

```javascript
const firebaseConfig = {
    apiKey: "SUA_API_KEY",
    authDomain: "SEU_PROJETO.firebaseapp.com",
    projectId: "SEU_PROJETO",
    storageBucket: "SEU_PROJETO.firebasestorage.app",
    messagingSenderId: "SEU_ID",
    appId: "SEU_APP_ID",
    measurementId: "SEU_MEASUREMENT_ID"
};
```

### 3. Ativar Autenticação

No Firebase Console → **Authentication** → **Sign-in method**, ative:

- ✅ **Anônimo** (para colaboradores acessarem o sistema)
- ✅ **E-mail/Senha** (para login dos técnicos de TI)

Em seguida, cadastre os usuários técnicos em **Authentication** → **Users** → **Add User**.

> **Dica:** O domínio de e-mail pode ser customizado. Por padrão, o sistema utiliza `@helpdeskti.com` e permite login apenas com o nome de usuário (sem digitar o domínio).

### 4. Configurar Firestore Rules

No Firebase Console → **Firestore Database** → **Rules**, cole as regras de segurança do projeto.

### 5. Configurar Storage Rules

No Firebase Console → **Storage** → **Rules**, cole as regras de segurança do storage.

---

## 🚀 Implantação

### GitHub Pages

1. Faça upload do `index.html` para um repositório público no GitHub.
2. Em **Settings** → **Pages**, selecione a branch `main` como source.
3. O sistema estará disponível em `https://seu-usuario.github.io/nome-do-repo/`.

### Execução Local

Por se tratar de um arquivo HTML único com dependências via CDN, basta abrir o `index.html` diretamente no navegador. Não é necessário servidor local, build ou instalação de dependências.

---

## 👥 Perfis de Acesso

### Colaboradores (Acesso Anônimo)
- Informam **unidade** e **setor** na primeira vez para filtrar os chamados relevantes.
- Podem abrir chamados, enviar mensagens no chat, contestar finalizações e usar o chat global.
- **Não podem:** acessar inventário, relatórios, kanban, checklists ou chat interno entre técnicos.

### Técnicos de TI (Login com E-mail/Senha)
- Acesso completo ao sistema: dashboard, inventário, relatórios, kanban, base de conhecimento, checklists e avisos.
- Podem gerenciar chamados (atribuir, alterar status/prioridade, finalizar).
- Acesso ao chat interno entre técnicos e chat global com todos os setores.

---

## 🔒 Segurança

- **Autenticação** gerenciada pelo Firebase Authentication com dois provedores (anônimo e e-mail/senha).
- **Firestore Security Rules** com função `isTechnician()` baseada em `sign_in_provider == 'password'` para distinguir colaboradores de técnicos.
- **Restrição de campos:** colaboradores só podem alterar campos específicos nos chamados (mensagens, status para contestação e histórico).
- **Coleções administrativas** (inventário, kanban, base de conhecimento, checklists) acessíveis exclusivamente por técnicos autenticados.
- **Storage** com validação de tipo de arquivo (somente imagens para colaboradores) e limite de tamanho (5MB para chat, 10MB para anexos administrativos).
- **Persistência de sessão** via `browserLocalPersistence` do Firebase Auth.

---

<p align="center">
  Desenvolvido com 💙 para equipes de TI que fazem a diferença.
</p>
