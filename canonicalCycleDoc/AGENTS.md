# CANONICAL CYCLE
## Diretrizes para Agentes de IA

---

## 📁 Estrutura Organizada por Role

As diretrizes estão organizadas em arquivos separados para melhor manutenção e uso:

### 🔄 Fluxo e Regras Fundamentais (Sempre Incluir)
- **[agents/canonicalCycle.md](./agents/canonicalCycle.md)** - Instruções completas do fluxo Canonical Cycle para agentes

### 🎭 Diretrizes por Role
- **[agents/analista.md](./agents/analista.md)** - 🧠 Agente de Análise
- **[agents/designer.md](./agents/designer.md)** - 🎨 Agente de Designer
- **[agents/arquiteto.md](./agents/arquiteto.md)** - 🏗️ Agente de Arquitetura
- **[agents/engenheiro.md](./agents/engenheiro.md)** - ⚙️ Agente de Engenharia
- **[agents/desenvolvedor.md](./agents/desenvolvedor.md)** - 💻 Agente de Desenvolvimento

---

## 🚀 Como Usar

### Para uma Role Específica

1. **Sempre inclua o fluxo e regras fundamentais:**
   - `agents/canonicalCycle.md`

2. **Inclua a diretriz específica da role:**
   - `agents/[role].md` (ex: `agents/analista.md`)

### Exemplo de Prompt

```
Você é um Agente de [Role] do Canonical Cycle.

Siga as diretrizes em:
- agents/canonicalCycle.md (fluxo e regras fundamentais)
- agents/[role].md (diretrizes específicas)

[seu prompt específico aqui]
```

---

---

## 📝 Estrutura de Pastas

```
archives/
└── [numero]_[nome_ciclo]/
    └── [role]/
        ├── raw/
        ├── filter/
        ├── canonical/
        └── artifacts/
```

**Exemplo:**
```
archives/
└── 6_nova_feature/
    └── analista/
        ├── raw/
        ├── filter/
        ├── canonical/
        └── artifacts/
```

---

## ⚠️ Nota

**Este arquivo é um índice de redirecionamento para agentes de IA.** 

Para as diretrizes completas, consulte:
- `agents/canonicalCycle.md` - Instruções do fluxo e regras fundamentais
- `agents/[role].md` - Diretrizes específicas de cada role

**Para humanos:** Consulte [README.md](./README.md) e [GUIDELINES.md](./GUIDELINES.md) para documentação voltada a humanos.
