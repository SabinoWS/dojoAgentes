---
description: Inicializa a pasta archive do projeto se não existir
---

# Canonical Init

Este workflow verifica e inicializa o diretório base para o Canonical Cycle.

1. Verificar se a pasta `archives` existe.
2. Se não existir, criar a pasta `archives`.

```bash
mkdir -p archives
echo "Pasta 'archives' verificada/criada com sucesso."
```
