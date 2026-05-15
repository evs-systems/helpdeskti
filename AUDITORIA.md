# Relatório de Auditoria e Hardening - HelpDesk TI

Este documento detalha todas as melhorias de segurança, modernização de stack e endurecimento de regras aplicadas ao projeto HelpDesk TI.

## 1. Melhorias de Segurança (Hardening)

### Content Security Policy (CSP)
- **Implementação:** Adicionada meta tag CSP robusta no `index.html`.
- **Objetivo:** Prevenir ataques de XSS (Cross-Site Scripting) e exfiltração de dados.
- **Domínios Permitidos:** Scripts e conexões limitados a domínios confiáveis como Google (Firebase, reCAPTCHA), ESM.sh, JSDelivr e Google Fonts.

### Firebase App Check
- **Provedor:** Integrado o **reCAPTCHA Enterprise**.
- **Impacto:** Protege o backend (Firestore/Storage) contra bots, scripts automatizados e acessos não autorizados fora da aplicação oficial.
- **Configuração:** O selo flutuante foi ocultado via CSS para melhorar a UI, e o aviso legal obrigatório foi adicionado aos formulários de Login e Abertura de Chamado para conformidade com os Termos de Serviço do Google.

## 2. Modernização da Stack

### Core
- **React:** Atualizado para a versão **18.3.1**.
- **Tailwind CSS:** Migrado para a **v4** (utilizando o novo browser engine `@tailwindcss/browser`).
- **Lucide React:** Atualizado para a versão **1.16.0**. Foi implementada uma camada de aliases para manter compatibilidade com nomes de ícones que mudaram na versão 1.0 (ex: `Lucide` -> `LucideIcon`).

### Performance e Dependências
- **CDN:** Versões fixas (pinning) para todas as bibliotecas externas para garantir estabilidade e segurança.
- **Firebase SDK:** Atualizado para **v11.7.1**.

## 3. Auditoria de Security Rules (Firestore)

As regras foram validadas e endurecidas para prevenir vulnerabilidades críticas detectadas:

- **Impersonificação:** Corrigida vulnerabilidade onde qualquer usuário logado poderia criar chamados em nome de outro (`userId` agora é validado contra `request.auth.uid`).
- **Manipulação de Status:** Colaboradores não podem mais finalizar chamados ou alterar prioridades. Apenas técnicos têm permissão de `update` total.
- **Integridade do Chat:** Validado para que apenas o autor da mensagem (ou o técnico responsável) possa enviar mensagens.
- **Campos Protegidos:** Implementada verificação de `affectedKeys()` para garantir que campos sensíveis como `createdAt` e `technician` não sejam alterados indevidamente.

## 4. Auditoria de Storage Rules

- **Tipo de Arquivo:** Restrito estritamente a imagens (`image/.*`).
- **Tamanho:** Limite máximo de **5MB** por upload.
- **Permissões:** Apenas técnicos podem deletar anexos. Colaboradores podem ler anexos de qualquer chamado (necessário para o histórico), mas só podem criar no caminho correspondente ao chamado.

## 5. Itens Não Alterados / Backlog

- **Modo Monolítico:** A estrutura de arquivo único (`index.html`) foi mantida conforme solicitado para facilitar a manutenção direta, utilizando Babel para transpilação em tempo de execução.
- **Custom Claims:** Para uma segurança ainda mais granular (ex: restringir chamados por Unidade/Departamento no nível do servidor), recomenda-se a implementação futura de *Custom Claims* no Firebase Auth.

---
**Status Final:** Sistema endurecido, modernizado e em conformidade técnica e legal.
