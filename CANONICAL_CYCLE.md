# Canonical Cycle

---

## Visão Geral

O **Canonical Cycle** é um fluxo de trabalho controlado no qual informações brutas são processadas por IA, validadas por humanos e consolidadas em material canônico antes da geração de artefatos e entrega de software.

### Três Pilares Fundamentais

O Canonical Cycle é sustentado por três pilares essenciais:

1. **🏗️ Bancada de Trabalho (Workspace Agent)**
   - Fornece contexto para a code base e entendimento do produto
   - Agentes precisam entender o código, estrutura do projeto, contexto técnico
   - Disponível durante todo o processo do Canonical Cycle

2. **🔄 Fluxo de Trabalho/Regras (Canonical Cycle Agent)**
   - Define e executa o fluxo de trabalho, regras de artefatos, personas e skills
   - Gerencia o Canonical Cycle, aplica regras, segue personas e usa skills específicas
   - Define o comportamento e fluxo dos agentes em cada etapa

3. **🌐 Contextos Abertos/Externos (MCPs)**
   - Acessa dados e conhecimentos de fontes externas
   - Sistemas externos (Jira, Confluence, etc.) e conhecimentos que não estão no workspace
   - Disponível quando agentes precisam de informações externas durante o processo

**Exemplo de contexto externo:** No meio do fluxo de trabalho, o agente precisa pegar dados no Jira ou conhecimentos de funcionamento da empresa de produtos que não estão no workspace.

### Princípio Fundamental

Cria um contrato explícito entre IA e humano:
- **IA nunca decide verdade** - apenas propõe interpretações
- **Humano nunca reinterpreta material bruto sem IA** - usa o fluxo estruturado
- **Canonical Material é o ponto de responsabilidade** - onde a verdade é estabelecida

---

## Fluxo do Canonical Cycle

```
Raw Material
   -> Filtered Material
      -> Canonical Material
         -> Artifacts
            -> Delivery
```

**`->`** = revisão / decisão humana explícita

**Regra de reentrância:** Qualquer alteração relevante → novo Canonical Cycle

---

## Estágios do Ciclo

### 🧱 Raw Material
Dados brutos e não estruturados, coletados sem interpretação.
- Anotações livres, atas de reunião, entrevistas, imagens, etc.
- **Nenhuma validação, nenhuma verdade assumida**

### 🔍 Filtered Material
Material interpretado e estruturado pela IA a partir do Raw Material.
- Resumos, agrupamentos, hipóteses, ambiguidades identificadas
- **Ainda não é oficial - é uma proposta de entendimento**

### 🏛️ Canonical Material
Material revisado, ajustado e aprovado por humano.
- Fonte oficial de verdade para as próximas etapas
- **Aqui a ambiguidade termina**

### 📄 Artifacts
Representações formais de entregáveis reais, ainda não publicadas.
- Tickets, documentos, planos técnicos, etc.
- **Prontos para entrega, aguardando publicação**

### 🚀 Delivery
Criação efetiva do artefato no sistema de destino.
- Criar ticket no Jira, abrir PR, publicar documento, deploy, etc.

---

## Quick Start

### 🚀 Iniciando um Novo Ciclo

**Opção 1: Usando o Assistente de Inicialização (Recomendado)**

Use o assistente que pergunta o nome do ciclo e a role:

1. **No Cursor ou outra ferramenta de IA:**
   - Use o prompt em [INICIALIZACAO.md](./INICIALIZACAO.md)
   - O assistente perguntará o nome do ciclo e a role
   - A estrutura será criada automaticamente

### 📋 Fluxo de Trabalho

3. **Colete Raw Material** na pasta `raw/` da role (ex: `archives/1_nova_feature/analista/raw/`)
4. **Use um agente de IA** para gerar Filtered Material na pasta `filter/` da mesma role (veja [AGENTS.md](./AGENTS.md))
5. **Revise e aprove** o Filtered Material como Canonical Material em `canonical/` da role (veja [GUIDELINES.md](./GUIDELINES.md))
6. **Gere artefatos** a partir do Canonical Material:
   - Artefatos em `archives/nome_ciclo/role/artifacts/` OU
   - Alterações diretas no projeto atual (fora de `archives/`)
7. **Passe artefatos para próxima role** (se houver) copiando/referenciando em `raw/` da próxima role
8. **Execute o Delivery** publicando os artefatos ou implementando as mudanças

Para um exemplo completo, veja [examples/analysis-cycle/](./examples/analysis-cycle/).

**Nota:** Para instruções técnicas sobre como agentes devem trabalhar, consulte [AGENTS.md](./AGENTS.md) e [agents/canonicalCycle.md](./agents/canonicalCycle.md).

---

## Estrutura do Repositório

```
canonicalCycle/
├── README.md              # Este arquivo
├── AGENTS.md              # Diretrizes para agentes de IA
├── GUIDELINES.md           # Diretrizes para humanos
├── templates/              # Templates para cada estágio
│   ├── raw-material-template.md
│   ├── filtered-material-template.md
│   ├── canonical-material-template.md
│   └── artifacts/
├── examples/               # Exemplos completos
│   ├── analysis-cycle/
│   ├── architecture-cycle/
│   └── engineering-cycle/
└── archives/              # Memória dos ciclos (separado do projeto)
    └── numeracao_nome_ciclo/
        ├── analista/
        │   ├── raw/
        │   ├── filter/
        │   ├── canonical/
        │   └── artifacts/
        ├── designer/ (quando necessário)
        │   ├── raw/
        │   ├── filter/
        │   ├── canonical/
        │   └── artifacts/
        ├── arquiteto/ (quando necessário)
        │   ├── raw/
        │   ├── filter/
        │   ├── canonical/
        │   └── artifacts/
        ├── engenheiro/
        │   ├── raw/
        │   ├── filter/
        │   ├── canonical/
        │   └── artifacts/
        └── desenvolvedor/
            ├── raw/
            ├── filter/
            ├── canonical/
            └── artifacts/
```

**Importante:** 
- A pasta `archives/` **NÃO faz parte do projeto** - é separada e serve apenas como memória e rastreabilidade dos ciclos. O projeto atual (fora de `archives/`) é onde o trabalho real acontece.
- Cada role tem suas próprias pastas (raw, filter, canonical, artifacts) dentro do ciclo
- Roles opcionais (Designer, Arquiteto) só têm pasta quando necessárias
- Numeração de arquivos é independente por role (cada role começa do 1)

---

## Fluxo Sequencial por Role

O Canonical Cycle segue um **fluxo sequencial** entre roles, onde os artefatos de uma role se tornam parte do Raw Material da próxima:

```
Analista → Designer (opcional) → Arquiteto (opcional) → Engenheiro → Desenvolvedor
```

**Fluxos possíveis:**
- Analista → Designer → Arquiteto → Engenheiro → Desenvolvedor (quando ambos são necessários)
- Analista → Designer → Engenheiro → Desenvolvedor (quando Arquiteto não é necessário)
- Analista → Arquiteto → Engenheiro → Desenvolvedor (quando Designer não é necessário)
- Analista → Engenheiro → Desenvolvedor (quando ambos são desnecessários)

**Transição entre roles:**
- Artefatos de uma role (ex: `analista/artifacts/`) são copiados ou referenciados na pasta `raw/` da próxima role (ex: `designer/raw/`)
- Cada role mantém seu próprio ciclo completo (raw → filter → canonical → artifacts)

### 🧠 Role: Analista

**Fluxo:**
```
Raw Material -> Filtered Material -> Canonical Material -> Analysis Artifacts
```

**Definições:**
- **Raw:** Conversa com cliente, anotações, fotos, documentos, relatos, prints
- **Filtered:** IA organizando e estruturando o Raw Material
- **Canonical:** Material aprovado pelo analista responsável
- **Artifacts:** Análise de negócio, requisitos, épicos e histórias

**Saída:** Artefatos passam para a próxima role (Designer ou Arquiteto)

### 🏗️ Role: Arquiteto

**Fluxo:**
```
Raw Material -> Filtered Material -> Canonical Material -> Architecture Artifacts
```

**Definições:**
- **Raw:** Artefato da role anterior (Análise) + coisas raw de levantamentos próprios do arquiteto
- **Filtered:** IA organizando e estruturando
- **Canonical:** Material aprovado pelo arquiteto responsável
- **Artifacts:** Artefatos arquiteturais (ADRs, diagramas, decisões técnicas)

**Saída:** Artefatos passam para a próxima role (Engenheiro)

**Observação:** Pode não ser necessário em todos os cenários (exemplo: correção de bugs simples)

### 🎨 Role: Designer

**Fluxo:**
```
Raw Material -> Filtered Material -> Canonical Material -> Design Artifacts
```

**Definições:**
- **Raw:** Artefatos da role anterior (Análise) + requisitos de UX/UI
- **Filtered:** Protótipos e designs estruturados pela IA
- **Canonical:** Protótipos aprovados pelo designer responsável
- **Artifacts:** Protótipos de tela, designs, links Figma, prints

**Características:**
- Recebe artefatos da role anterior (Análise) como parte do Raw Material
- Foco em protótipos de tela e experiência do usuário
- Artefatos passam para a próxima role (Arquiteto ou Engenheiro)

**Saída:** Protótipos aprovados passam para a próxima role (Arquiteto ou Engenheiro)

**Observação:** Pode não ser necessário em todos os cenários (exemplo: funcionalidades backend, correções simples, melhorias técnicas, quando design já está estabelecido)

### ⚙️ Role: Engenheiro

**Fluxo:**
```
Raw Material -> Filtered Material -> Canonical Material -> Engineering Artifacts
```

**Definições:**
- **Raw:** Tickets/artefatos da role anterior + contexto de workspace (código)
- **Filtered:** Levantamento filtrado sobre ajustes, impactos, esforço e onde mexer exatamente
- **Canonical:** Tasks detalhadas aprovadas
- **Artifacts:** Tickets no Jira com tasks detalhadas

**Características:**
- Agente lê tickets anteriores e código do workspace
- Cria análise técnica (impactos, esforço, localização exata das mudanças)

**Saída:** Tasks detalhadas passam para a próxima role (Desenvolvedor)

### 💻 Role: Desenvolvedor

**Fluxo:**
```
Raw Material -> Filtered Material -> Canonical Material -> Artifacts
```

**Definições:**
- **Raw:** Tasks (recebidas da role anterior)
- **Filtered:** Alterações no workspace (código) feitas pelo agente
- **Canonical:** Stage do git (código pronto para commit)
- **Artifacts:** Commit

**Características:**
- Foco em implementação de código
- Filtered = código gerado/modificado pelo agente
- Canonical = código revisado e staged no git
- Artifact = commit final

**Saída:** Entrega real (código commitado, tickets criados, PRs abertos, etc.)

---

## Conceitos Importantes

### Memória por Arquivo
- Cada arquivo mantém sua própria memória/contexto através da estrutura `archives/`
- Permite rastreabilidade e histórico por arquivo
- Facilita geração de artefatos a partir de canonicals específicos

### Artefatos Descartáveis
- Artefatos podem ser gerados a qualquer momento a partir do Canonical Material
- Artefatos são descartáveis (podem ser regenerados)
- Canonical Material é a fonte de verdade, não os artefatos

### Autonomia Agentica com Responsabilidade Técnica
- Agentes têm autonomia para processar e gerar
- Responsabilidade técnica fica com as personas que aprovam os canonicals
- Uma mesma pessoa pode atuar em múltiplas personas/roles

### Destinos do Canonical Material

O Canonical Material pode ter **dois destinos**:

1. **Gerar artefatos na pasta `artifacts/`**
   - Artefatos são representações formais (tickets, documentos, etc.)
   - Ficam em `archives/nome_ciclo/artifacts/`
   - São descartáveis e podem ser regenerados
   - Usados para referência ou publicação em sistemas externos

2. **Alterar o projeto atual (fora do `archives/`)**
   - Mudanças diretas no código, documentação ou estrutura do projeto
   - Exemplos: atualizar README.md, modificar código, criar novos arquivos
   - Essas mudanças são permanentes no projeto
   - Implementações diretas baseadas no Canonical Material

Ambos os destinos podem ser usados simultaneamente.

---

## Regras Fundamentais

1. ❌ **Nada gera artefato sem Canonical Material**
2. ❌ **Canonical Material não nasce da IA sozinho** - requer aprovação humana
3. ✅ **Toda decisão tem um ponto humano explícito**
4. 🔁 **Mudou o contexto? Novo ciclo**
5. 📌 **Artefatos sempre referenciam um Canonical**
6. 🔄 **Artefatos de uma role se tornam Raw da próxima** (fluxo sequencial)
7. 🎨 **Designer e Arquiteto são roles opcionais** - podem ser puladas conforme necessidade

---

## Documentação

### Para Humanos
- **[README.md](./README.md)** - Este arquivo (filosofia e visão geral)
- **[examples/](./examples/)** - Exemplos completos de uso

### Para Agentes de IA
- **[AGENTS.md](./AGENTS.md)** - Índice de diretrizes para agentes
- **[agents/canonicalCycle.md](./agents/canonicalCycle.md)** - Instruções completas do fluxo para agentes
- **[agents/[role].md](./agents/)** - Diretrizes específicas por role