---
description: Workflow de auditoria e refinamento de apresentações Marp, focado em layout e "perfeccionismo".
---

# 🕵️ Workflow: Revisar Apresentação (Marp)

Este fluxo executa uma revisão detalhada no arquivo de slides atual, buscando imperfeições visuais, problemas de layout e oportunidades de melhoria estética.

## 1. 📖 Leitura e Carregamento
1.  Identifique o arquivo de apresentação alvo (padrão: `slides.md`).
2.  Leia o conteúdo completo do arquivo.
3.  Carregue as regras da skill **Marp Slides Perfectionist** (`.agent/skills/marp-slides-perfectionist/SKILL.md`) para usar como critério de avaliação.

## 2. 🔍 Análise "Pente Fino"
Analise o markdown procurando por:
1.  **Slides Superlotados**: Slides com mais de 7 itens de lista ou parágrafos muito longos que provavelmente estouram a tela.
2.  **Problemas de Contraste**: Uso de imagens de fundo sem filtros (ex: `brightness`) ou sem ajuste de cor de texto.
3.  **Sintaxe Marp**: Uso incorreto ou sub-otimizado de diretivas (ex: falta de paginação, temas misturados).
4.  **Imagens**: Imagens que podem estar distorcidas ou ocupando espaço demais.

## 3. 📝 Relatório Interativo
Para cada problema potencial encontrado, apresente ao usuário:
*   **Slide**: (Número ou Título)
*   **O Problema**: "Texto provavelmente estourando a altura do slide."
*   **Sugestão do Perfeccionista**: "Quebrar em dois slides ou reduzir a imagem lateral para 30%."

**Exemplo de Interação:**
> "No Slide 3 ('Arquitetura'), notei que há 12 tópicos. Isso vai cortar na tela.
> 1. Quebrar em dois slides?
> 2. Tentar resumir?
> 3. Ignorar?
> O que prefere?"

## 4. 🛠️ Execução de Melhorias
1.  Conforme o usuário aprovar as sugestões, aplique as correções.
2.  **Regra de Ouro**: Ao aplicar correções, use a skill *Perfectionist* para garantir que a sintaxe (ex: `![bg right:33%]`) esteja correta.
3.  Não mude o *sentido* do texto, apenas a *forma* (layout, quebras, estilos).

## 5. ✅ Finalização
1.  Após passar por todos os pontos, mostre um resumo das alterações.
2.  Pergunte se o usuário quer ver o diff final ou salvar (o agente deve gerenciar o salvamento no arquivo).
