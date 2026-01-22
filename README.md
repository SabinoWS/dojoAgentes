# Dojo de Agentes, Antigravity & Engenharia de Software

Este repositório é dedicado a um **Dojo Baby Steps**, focado no repasse de conhecimento prático sobre a configuração de Agentes de IA, seus métodos e fluxos de trabalho (com ênfase no **Antigravity** do Google).

Aqui vamos explorar, degrau por degrau, conceitos fundamentais e a aplicação do **Canonical Cycle** para análise e desenvolvimento de soluções.

---

## 🏗️ Tópicos Abordados

### 🤖 Agentes & Antigravity
Sistemas autônomos que atuam como pares de trabalho, capazes de executar comandos, manipular arquivos e raciocinar sobre tarefas complexas. O foco é sair do modelo "chatbot" para o modelo "agente executor".

### 🛠️ Configuração: Rules, Skills & Workflows
A estrutura modular que dá vida ao agente:
*   **Rules**: O contexto imutável e regras de segurança (o que *não* fazer).
*   **Skills**: Ferramentas e habilidades técnicas (como usar git, como fazer deploy).
*   **Workflows**: Processos passo-a-passo para tarefas repetitivas.

### 📜 SDD (Spec Driven Development)
Metodologia onde o **Markdown** serve como contrato e API entre humano e IA. Em vez de chats efêmeros, escrevemos especificações claras (`Specs`) que o agente lê e implementa, garantindo fidelidade aos requisitos.

### 🧠 Memória por Arquivo
A filosofia de que "se não está num arquivo, não existe". Abandonamos a memória volátil do chat em favor da persistência documental na codebase.

### 🔌 MCP (Model Context Protocol)
O padrão aberto que conecta a IA ao mundo externo. Permite que o agente acesse com segurança dados do **Jira**, **Confluence**, **Bancos de Dados** e **Web**, expandindo seu contexto além do editor de código.

### 🔄 O Canonical Cycle
Um framework de trabalho para garantir consistência e verdade no desenvolvimento com IA.
*   **Fluxo**: `Raw` (Bruto) → `Filtered` (Organizado) → `Canonical` (Verdade Aprovada) → `Artifacts` (Produtivos) → `Delivery` (Entrega).
*   **Filosofia**: A IA propõe, o Humano aprova (torna canônico), e a partir daí a execução é determinística.

---

## 🎯 Objetivo
Servir como guia prático e base de conhecimento para o time iniciar na **Engenharia de Software Agêntica**.
