---
description: Continua um ciclo Canonical existente.
---

# Canonical Cycle Continue

Este workflow ajuda a retomar um ciclo de trabalho que foi interrompido ou pausado.

## Passos para o Agente

1.  **Identificar Ciclos Existentes:**
    *   Liste o conteúdo da pasta `archives/` para ver quais ciclos estão disponíveis.
    *   Apresente a lista para o usuário.

2.  **Solicitar Ciclo Alvo:**
    *   Pergunte ao usuário qual ciclo ele deseja continuar (pelo número ou nome).
    *   Pergunte qual Role, se houver ambiguidade (se houver mais de uma role dentro do ciclo).

3.  **Diagnosticar Estado:**
    *   Verifique as pastas do ciclo escolhido (`raw`, `filter`, `canonical`, `artifacts`).
    *   Tente identificar onde o trabalho parou:
        *   Se `canonical/` tem arquivos recentes -> Provável fase de Artefatos ou Delivery.
        *   Se `filter/` tem arquivos recentes -> Provável fase de Canonical. 
            *   **IMPORTANTE:** Leia os arquivos em `filter/` e verifique se há perguntas não respondidas ou termos como "TODO", "PENDENTE", "RESPONDER". Se houver, alerte o usuário que a fase de Filtro pode não estar concluída.
        *   Se `raw/` tem arquivos mas `filter/` está vazio -> Fase de Filtro.
    *   Informe ao usuário o estado encontrado: "Parece que paramos na fase X (baseado nos arquivos Y)."

4.  **Confirmar Reinício:**
    *   Pergunte: "Está correto? De onde você gostaria de retomar?"
    *   Opções sugeridas:
        *   Continuar do ponto detectado.
        *   Refazer etapa anterior.

5.  **Ação de Retomada:**
    *   Carregue a **SKILL da Role** correspondente (Analista, Dev, etc).
        *   Ex: `view_file .agent/skills/analista/SKILL.md`
    *   Carregue o último arquivo relevante (o state atual).
    *   Siga as instruções da skill `canonical-cycle` para o próximo passo lógico.
