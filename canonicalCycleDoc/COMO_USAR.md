# Como Usar as Diretrizes de Agentes em Diferentes Ferramentas

Este documento explica como usar as diretrizes de agentes separadas por role em diferentes ferramentas de IA (Cursor, Gemini, Claude, etc.).

---

## 📋 Estrutura de Arquivos

```
agents/
├── canonicalCycle.md  # Instruções do fluxo (sempre incluir)
├── analista.md        # Diretrizes específicas do Analista
├── designer.md        # Diretrizes específicas do Designer
├── arquiteto.md       # Diretrizes específicas do Arquiteto
├── engenheiro.md      # Diretrizes específicas do Engenheiro
└── desenvolvedor.md    # Diretrizes específicas do Desenvolvedor
```

---

## 🔄 Fluxo Recomendado

### Identificar a Role

Determine qual role você está usando:
- Analista
- Designer
- Arquiteto
- Engenheiro
- Desenvolvedor

### Carregar Diretrizes

**Se a ferramenta não ler os mds, inclua:**
- `agents/canonicalCycle.md` (fluxo e regras fundamentais)

**Inclua também:**
- `agents/[role].md` (diretrizes específicas da role)

### Prompt

```
Você é um Agente de [Role] do Canonical Cycle.

Siga as diretrizes em:
- agents/canonicalCycle.md
- agents/[role].md

[seu prompt específico]
```

---

## 🔗 Links Úteis

- [README.md](../README.md) - Visão geral do projeto
