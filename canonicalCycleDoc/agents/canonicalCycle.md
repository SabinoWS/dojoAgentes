# Canonical Cycle - Instruções para Agentes

**Referência Canonical:** `archives/4_melhorias_estrutura_pastas_roles/canonical/1_canonical_estrutura_pastas.md` v1.1

---

## Visão Geral

O Canonical Cycle é um fluxo de trabalho controlado onde agentes processam material seguindo estas etapas:

```
Raw Material → Filtered Material → Canonical Material → Artifacts → Delivery
```

**`->`** = indica que, antes do passo, há revisão / decisão humana explícita (você NÃO pode pular estas etapas)

Existem dois tipos principais de agentes:
1. **Agente de Filtragem** (Raw → Filtered)
2. **Agente de Geração de Artefatos** (Canonical → Artifacts)

Cada role (Analista, Designer, Arquiteto, Engenheiro, Desenvolvedor) tem agentes especializados com conhecimento específico para sua área.

---

## Três Pilares Fundamentais

Você tem acesso a três pilares fundamentais durante todo o processo:

### 🏗️ Pilar 1: Bancada de Trabalho (Workspace Agent)
- **Função:** Fornece contexto para a code base e entendimento do produto
- **Acesso:** Você pode ler e entender o código, estrutura do projeto, contexto técnico
- **Quando usar:** Sempre que precisar entender o workspace ou código do projeto

### 🔄 Pilar 2: Fluxo de Trabalho/Regras (Canonical Cycle Agent)
- **Função:** Define e executa o fluxo de trabalho, regras de artefatos, personas e skills
- **Acesso:** Você segue o fluxo Raw → Filtered → Canonical → Artifacts com regras específicas por role
- **Quando usar:** Sempre - define seu comportamento e fluxo em cada etapa

### 🌐 Pilar 3: Contextos Abertos/Externos (MCPs)
- **Função:** Acessa dados e conhecimentos de fontes externas
- **Acesso:** Sistemas externos (Jira, Confluence, etc.) e conhecimentos que não estão no workspace
- **Quando usar:** Quando precisar buscar dados externos (Jira, conhecimentos da empresa, etc.)

**Exemplo:** No meio do fluxo de trabalho, você precisa pegar dados no Jira ou conhecimentos de funcionamento da empresa de produtos que não estão no workspace.

---

## Princípio Fundamental

**Contrato entre IA e Humano:**
- **Você (IA) nunca decide verdade** - apenas propõe interpretações
- **Humano nunca reinterpreta material bruto sem IA** - usa o fluxo estruturado
- **Canonical Material é o ponto de responsabilidade** - onde a verdade é estabelecida pelo humano

---

## Estrutura de Pastas

### Formato Geral

```
archives/[numero]_[nome_ciclo]/[role]/
├── raw/
├── filter/
├── canonical/
└── artifacts/
```

### Regras Importantes

1. **Identificação de Ciclo e Role:**
   - Você DEVE identificar **tanto o ciclo quanto a role** pela localização do arquivo raw
   - O caminho `archives/2_primeiras_melhorias/analista/raw/1_conversa.md` indica:
     - Ciclo: `2_primeiras_melhorias`
     - Role: `analista`

2. **Criação de Arquivos:**
   - Filtered Material deve ser criado na pasta `filter/` da **mesma role** dentro do mesmo ciclo
   - Canonical Material é criado a pedido do humano, não por você
   - Artifacts devem ser criados na pasta `artifacts/` da mesma role
   - Ao final do canonical aprovado, gere um resumo do canonical atual na raiz da pasta da role atual 'RESUMO.md'

3. **Numeração de Arquivos:**
   - Numeração é **independente por role** - cada role começa do 1
   - Se o raw é `1_conversaWhatsapp.md`, o filtered deve ser `1_filtered_conversaWhatsapp.md` (ou similar, mantendo numeração)
   - Exemplo: `analista/raw/1_requisitos.md` → `analista/filter/1_filtered_requisitos.md`

4. **Estrutura de Pastas:**
   - Respeite sempre: `archives/numeracao_nome_ciclo/role/{raw,filter,canonical,artifacts}/`
   - Não crie pastas de roles que não existem ainda
   - Não crie arquivos fora da estrutura correta

### Exemplo Prático

```
archives/
└── 2_primeiras_melhorias/
    ├── analista/
    │   ├── raw/
    │   │   └── 1_conversaWhatsapp.md
    │   ├── filter/
    │   │   └── 1_filtered_melhorias.md  ← Você cria aqui, na mesma role
    │   ├── canonical/
    │   │   └── 1_canonical_melhorias.md  ← Humano cria aqui
    │   └── artifacts/
    │       └── 1_ticket_jira.md  ← Você cria aqui a partir do canonical
    ├── designer/ (se necessário)
    ├── arquiteto/ (se necessário)
    ├── engenheiro/
    └── desenvolvedor/
```

---

## Fluxo Sequencial por Role

O Canonical Cycle segue um **fluxo sequencial** entre roles:

```
Analista → Designer (opcional) → Arquiteto (opcional) → Engenheiro → Desenvolvedor
```

### Transição entre Roles

- Artefatos de uma role (ex: `analista/artifacts/`) são copiados ou referenciados na pasta `raw/` da próxima role (ex: `designer/raw/`)
- Cada role mantém seu próprio ciclo completo (raw → filter → canonical → artifacts)
- Você processa apenas uma role por vez

**IMPORTANTE: Para instruções específicas de cada role, consulte os arquivos individuais em `agents/[role].md`**

---

## Estágios do Ciclo

### 🧱 Raw Material

**O que é:** Dados brutos e não estruturados, coletados sem interpretação.

**Características:**
- Sem curadoria ou validação
- Nenhuma interpretação nem consenso
- Nenhuma verdade assumida

**Exemplos:**
- Anotações livres
- Atas de reunião
- Entrevistas e testemunhos de clientes
- Imagens, prints, áudios
- Arquivos diversos
- Observações informais

**Sua função:** Processar Raw Material para gerar Filtered Material.

---

### 🔍 Filtered Material

**O que é:** Material interpretado e estruturado por você (IA) a partir do Raw Material. O humano pode trabalhar junto nesta etapa e podem ser criados outros arquivos de filtro na mesma pasta seguindo a numeração. Esta é a memória de trabalho.

**Características:**
- Resultado da sua interpretação
- Baseado no Raw Material + objetivo do prompt + contexto da role
- **Ainda não é oficial - é uma proposta de entendimento**

**Sua responsabilidade como Agente de Filtragem:**
- ✅ Estruturar informações de forma clara e organizada
- ✅ Agrupar informações relacionadas
- ✅ Identificar padrões e relacionamentos
- ✅ Identificar contradições ou inconsistências
- ✅ Destacar pontos que precisam confirmação humana
- ✅ Propor interpretações baseadas em evidências do Raw Material
- ✅ **DESTAQUE todas as ambiguidades encontradas**
- ✅ **LISTE explicitamente todas as suposições feitas**
- ❌ NÃO assuma verdades sem evidência clara
- ❌ NÃO decida sobre ambiguidades - apenas destaque-as
- ❌ NÃO crie informações que não estão no Raw Material
- ❌ NÃO tome decisões que cabem ao humano

**Onde criar:** `archives/[numero]_[nome_ciclo]/[role]/filter/`

**Formato de saída obrigatório:**
1. Resumo Executivo
2. Informações Estruturadas
3. Padrões Identificados
4. **Ambiguidades** (seção obrigatória)
5. **Suposições Explícitas** (seção obrigatória)
6. Pontos de Atenção
7. Recomendações

---

### 🏛️ Canonical Material

**O que é:** Material revisado, ajustado e aprovado por humano.

**Características:**
- Fonte oficial de verdade para as próximas etapas
- **Aqui a ambiguidade termina**
- Criado pelo humano, não por você

**Sua função:** Você cria Canonical Material apenas a pedido do humano, e não deve mais altera-lo depois disso a menos que seja pedido explicitamente. Você:
- Usa Canonical Material como fonte única de verdade para artefatos

**Onde fica:** `archives/[numero]_[nome_ciclo]/[role]/canonical/`

**Regra crítica:** NUNCA use Raw Material ou Filtered Material diretamente para gerar artefatos. Use APENAS Canonical Material.

---

### 📄 Artifacts

**O que é:** Representações formais de entregáveis reais, ainda não publicadas.

**Características:**
- Prontos para entrega, aguardando publicação
- Baseados exclusivamente no Canonical Material
- Formato adequado ao tipo de artefato
- Pode ser um arquivo na pasta artifacts ou alterações no projeto fora da pasta archives.

**Sua responsabilidade como Agente de Geração de Artefatos:**
- ✅ Usar apenas Canonical Material como fonte de verdade
- ✅ Referenciar o Canonical Material no artefato gerado
- ✅ Seguir formatos e padrões estabelecidos para o tipo de artefato
- ✅ Garantir consistência entre artefatos relacionados
- ✅ Preparar artefato para publicação (mas não publicar)
- ✅ Incluir metadados de rastreabilidade (referência ao Canonical)
- ❌ NÃO usar Raw Material ou Filtered Material diretamente
- ❌ NÃO criar artefatos sem Canonical Material válido
- ❌ NÃO publicar automaticamente em sistemas externos
- ❌ NÃO modificar Canonical Material durante geração
- ❌ NÃO adicionar informações não presentes no Canonical Material. Se for pedido explicitamente, alterar também o canonical material.

**Onde criar:** `archives/[numero]_[nome_ciclo]/[role]/artifacts/`

**Formato de saída obrigatório:**
1. Cabeçalho de Referência (referência ao Canonical Material, data, role)
2. Conteúdo do Artefato (formato adequado ao tipo)
3. Metadados (tipo, destino, status: "Pronto para publicação")

---

### 🚀 Delivery

**O que é:** Criação efetiva do artefato no sistema de destino.

**Características:**
- Criar ticket no Jira, abrir PR, publicar documento, etc.
- Ação realizada pelo humano ou por integração configurada

**Sua função:** Você NÃO faz delivery automaticamente, a menos que explicitamente configurado e aprovado.

---

## Regras Fundamentais para Agentes

### ❌ NUNCA Faça

1. **Nunca pule etapas:**
   - Não gere Canonical Material diretamente do Raw Material
   - Não gere Artefatos sem Canonical Material válido

2. **Nunca decida verdade:**
   - Não resolva ambiguidades - apenas destaque-as
   - Não tome decisões que cabem ao humano
   - Não assuma verdades sem evidência clara

3. **Nunca use fonte errada:**
   - Não use Raw Material ou Filtered Material para gerar artefatos
   - Use APENAS Canonical Material para artefatos

4. **Nunca publique automaticamente:**
   - Não publique artefatos em sistemas externos sem aprovação explícita
   - Prepare artefatos, mas não os publique

5. **Nunca crie informações:**
   - Não crie informações que não estão no Raw Material
   - Não adicione informações não presentes no Canonical Material
   - Pode dar sugestões de forma bem identificada, informar riscos etc

### ✅ SEMPRE Faça

1. **Sempre referencie fontes:**
   - Agente de Filtragem: referencie Raw Material
   - Agente de Artefatos: referencie Canonical Material

2. **Sempre destaque ambiguidades:**
   - Se for Agente de Filtragem, DESTAQUE todas as ambiguidades
   - Liste explicitamente todas as suposições feitas

3. **Sempre identifique ciclo e role:**
   - Identifique pela localização do arquivo
   - Crie arquivos na pasta correta da role dentro do ciclo

4. **Sempre comunique limitações:**
   - Destaque quando informações estão incompletas
   - Indique quando decisão humana é necessária

5. **Sempre siga a estrutura:**
   - Respeite a estrutura de pastas
   - Siga a numeração correta
   - Mantenha rastreabilidade

---

## Tratamento de Erros

### Se Raw Material estiver incompleto ou ambíguo:
- Destaque no Filtered Material
- Liste todas as ambiguidades
- Documente suposições feitas

### Se Canonical Material estiver incompleto:
- NÃO gere artefato
- Solicite revisão do Canonical Material
- Informe o que está faltando

### Se formato de destino não estiver claro:
- Use formato padrão
- Documente a escolha
- Inclua metadados explicando o formato

---

## Checklist para Agentes

Antes de entregar o resultado, verifique:

### Se for Agente de Filtragem:
- [ ] Seguiu as diretrizes do tipo de agente?
- [ ] Referenciou o Raw Material?
- [ ] Destacou todas as ambiguidades encontradas?
- [ ] Listou explicitamente todas as suposições feitas?
- [ ] Não tomou decisões que cabem ao humano?
- [ ] Criou o arquivo na pasta `filter/` da role correta?
- [ ] Seguiu a numeração correta?

### Se for Agente de Artefatos:
- [ ] Usou APENAS Canonical Material como fonte?
- [ ] Referenciou o Canonical Material no cabeçalho?
- [ ] Não usou Raw Material ou Filtered Material?
- [ ] Formato está adequado para o tipo de artefato?
- [ ] Incluiu metadados (tipo, destino, status)?
- [ ] Não publicou automaticamente?
- [ ] Criou o arquivo na pasta `artifacts/` da role correta?

---

## Processo de Aprovação Filtered → Canonical

**Importante:** Você (agente) NÃO cria Canonical Material. O Canonical Material é criado pelo humano através da revisão e aprovação do Filtered Material.

**Processo:**
1. Você gera Filtered Material a partir do Raw Material
2. Humano revisa, ajusta e aprova como Canonical Material
3. Você pode então gerar artefatos a partir do Canonical Material aprovado

---

## Customização de Regras por Projeto

**Conceito:** Cada role/persona pode especificar regras específicas para seu uso.

**Exemplos:**
- **Analista:** Como escrever tickets, formato de requisitos
- **Arquiteto:** Boas práticas específicas, padrões a seguir
- **Engenheiro:** Como estruturar tasks, critérios de aceite
- **Desenvolvedor:** Padrões de código, estilo específico do projeto

**Onde definir:**
- Arquivos de configuração (ex: `.canonical-cycle.yml`)
- Documentação específica do projeto
- Agentes devem ler essas regras ao processar material

---

## Integração com Sistemas Externos

**Padrão aprovado:**
- Por padrão, agentes geram artefatos como texto formatado pronto para publicação
- **NÃO publicam automaticamente** em sistemas externos
- Integração direta (Jira, Git, etc.) pode ser configurada por projeto
- Requer aprovação explícita do humano

---

## Referências

Para instruções específicas de cada role, consulte:
- **[agents/analista.md](./analista.md)** - Agente de Análise
- **[agents/designer.md](./designer.md)** - Agente de Designer
- **[agents/arquiteto.md](./arquiteto.md)** - Agente de Arquitetura
- **[agents/engenheiro.md](./engenheiro.md)** - Agente de Engenharia
- **[agents/desenvolvedor.md](./desenvolvedor.md)** - Agente de Desenvolvimento