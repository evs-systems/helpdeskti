# 🖥️ HelpDesk TI

Sistema completo de **Gestão de Chamados, Inventário e Organização** para equipes de Tecnologia da Informação. Desenvolvido como uma aplicação web single-page (SPA) com React e Firebase, hospedado gratuitamente no GitHub Pages.

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
- Visualização inteligente em **Grade ou Lista** (compacta) com preferências salvas por aba.
- Paginação otimizada com carregamento dinâmico em lote.
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
- **Importação inteligente** via CSV com Upsert (atualiza registros sem duplicar) e proteção anti-injection (CWE-1236).
- **Exportação** da lista filtrada para CSV.
- Histórico de movimentações por equipamento.

### 🧮 Controle de Acessórios
- Cadastro de acessórios (Mouse, Teclado, Fones, Cabos, etc.) com controle de estoque.
- **Movimentações**: entrada e saída de itens com registro de destino (unidade/setor).
- Visualização de movimentações por mês/ano com filtro por tipo de acessório.
- Agrupamento por item com resumo de entradas e saídas.

### 📹 Gestão de Câmeras
- Cadastro e monitoramento de câmeras de segurança do CFTV.
- Rotina de **verificação diária** para garantia de gravação e funcionamento.
- Histórico de revisões e alertas visuais de pendência.

### 📌 Quadro Kanban (Organização TI)
- Quadro de tarefas com colunas: **A Fazer**, **Em Andamento**, **Em Revisão** e **Concluído**.
- **Arrastar e soltar** (drag-and-drop) entre colunas.
- Detalhes com descrição, responsável, anexos e comentários.
- Upload de documentos e arquivos de apoio por tarefa.

### 📚 Base de Conhecimento
- Registro de **informações padrão** da equipe (senhas, procedimentos, links úteis).
- Busca por título ou conteúdo.
- Renderização rica e segura com **Markdown**.
- Visualizador de arquivos integrado e seguro (In-App Sandbox Viewer).
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

### 📄 Licença
Uso interno — Todos os direitos reservados.

---

<p align="center">
  Desenvolvido com 💙 por Kayck Lima©.
</p>
