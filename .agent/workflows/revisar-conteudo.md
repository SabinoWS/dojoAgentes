---
description: Workflow para revisão profunda de conteúdo, gramática e estrutura lógica de apresentações Marp.
---

# Workflow: Revisar Conteúdo de Apresentação

Este workflow foca na integridade do conteúdo, garantindo que o texto esteja correto, a lógica faça sentido e os índices estejam sincronizados.

## 1. Identificação e Leitura
1.  Identifique qual arquivo de apresentação (`.md`) o usuário deseja revisar. Se não estiver claro, pergunte.
2.  Utilize a ferramenta `view_file` para ler o conteúdo completo da apresentação.

## 2. Ativação da Skill de Revisão
1.  Leia e internalize as instruções da skill **Marp Slides Content Reviewer** localizada em:
    `/home/sabino/Desktop/projetos/dojoAgentes/.agent/skills/marp-slides-content-reviewer/SKILL.md`

## 3. Análise de Conteúdo (Checklist)
Com base na skill, analise o texto da apresentação procurando por:
*   **Erros de Português**: Gramática, ortografia e pontuação incorretas.
*   **Consistência de Índices**: Se houver um slide de "Agenda" ou "Índice", verifique se ele lista corretamente todos os tópicos/seções presentes nos slides subsequentes.
*   **Coerência de Resumos**: Se houver slides de resumo ou conclusão, verifique se eles refletem de fato o que foi apresentado.
*   **Fluxo Lógico**: Identifique se a ordem dos slides faz sentido narrativo.

## 4. Relatório e Interação
1.  Apresente ao usuário um resumo dos pontos de atenção encontrados (ex: "Encontrei 3 erros de digitação e o item X da Agenda não existe nos slides").
2.  Para cada grupo de problemas ou problema crítico, pergunte explicitamente: "Deseja que eu corrija estes pontos?".

## 5. Execução de Correções
1.  Após a confirmação do usuário, realize as edições no arquivo da apresentação usando `replace_file_content` (para edições simples) ou `multi_replace_file_content` (para múltiplas edições).
2.  Mantenha o usuário informado sobre o que está sendo alterado.
