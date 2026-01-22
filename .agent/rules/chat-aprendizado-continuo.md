---
description: Processo para identificar, confirmar e registrar aprendizados e correções do usuário na memória do agente.
---

# 🎓 Processo de Aprendizado Contínuo

Esta regra define como o agente deve lidar com correções do usuário ou novos aprendizados críticos.

## 🕵️ Detecção
O agente deve ficar atento quando:
1.  O usuário corrige explicitamente um comportamento ou saída do agente ("Não faça assim, faça assado", "Você errou X").
2.  O usuário reforça uma preferência importante.
3.  O agente identifica um "insight" ou técnica nova que é crucial para o contexto do projeto.

## 🗣️ Confirmação
Ao detectar um item acima, o agente **DEVE** perguntar ativamente ao usuário:
> "Percebi que isso é uma correção/aprendizado importante. Você gostaria que eu anote isso na minha memória (`chat-aprendizado-memoria`) para não errar novamente?"

## 📝 Registro (Se confirmado)
Se o usuário confirmar, o agente deve editar o arquivo `.agent/rules/chat-aprendizado-memoria.md` e adicionar uma nova entrada seguindo esta estrutura rigorosa:

```markdown
### [DATA] - Título Curto do Aprendizado
*   **Contexto**: Breve explicação do que aconteceu ou o que estava sendo feito.
*   **Correção/Lição**: O que deve ser feito (ou NÃO feito) a partir de agora.
*   **Porquê**: Motivo da correção (se aplicável).
---
```

## ⚠️ Importante
*   Mantenha o arquivo de memória limpo e organizado.
*   Não adicione coisas triviais sem perguntar.
*   Use a tool `write_to_file` (ou `replace/multi_replace`) para adicionar o bloco de texto ao final do arquivo de memória.
