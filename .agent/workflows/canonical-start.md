---
description: Inicia um novo ciclo Canonical. Cria estrutura e guia o usuário.
---

# Canonical Cycle Start

Este workflow orienta o Agente a iniciar um novo ciclo de trabalho no padrão Canonical Cycle.

## Passos para o Agente

1.  **Solicitar Informações (se não fornecidas):**
    *   Pergunte ao usuário qual a **Role** (analista, designer, arquiteto, engenheiro, desenvolvedor).
    *   Pergunte ao usuário o **Nome do Ciclo** (curto, sem espaços, ex: `nova_feature`).

2.  **Criar Estrutura:**
    *   Utilize o script da skill `canonical-cycle` para criar a estrutura de pastas automaticamente.
    *   Comando: `python3 .agent/skills/canonical-cycle/scripts/init_cycle.py <ROLE> <NOME_CICLO>`

3.  **Confirmar e Orientar:**
    *   Informe ao usuário onde as pastas foram criadas.
    *   Instrua claramente: "Por favor, adicione todos os arquivos brutos (notas, documentos, prints, áudios transcritos) na pasta `raw/` que foi criada."
    *   Oriente sobre o próximo passo: "Me avise assim que os arquivos estiverem lá. Nesse momento, faremos o filtro inicial, onde organizaremos o material e definiremos o que é realmente relevante para o ciclo."

4.  **Acompanhamento (Aguardando Usuário):**
    *   Aguarde a confirmação do usuário de que os arquivos foram adicionados.
    *   NÃO tente ler ou filtrar antes da confirmação do usuário, a menos que ele explicitamente peça.

5.  **Gerar Filtered & Validar Ambiguidades:**
    *   **Carregar Skill da Role:** Utilize a ferramenta `view_file` para ler a skill específica da role escolhida (ex: `.agent/skills/analista/SKILL.md`) para entender as diretrizes de filtro específicas.
    *   Processe o material Raw e gere o arquivo na pasta `filter/`.
    *   Caso existam ambiguidades, destaque-as em uma seção "Pontos para Definição".
    *   **IMPORTANTE:** Adicione o texto `RESPOSTA:` abaixo de cada pergunta ou ponto de ambiguidade no arquivo, para indicar onde o usuário deve responder caso opte por editar o arquivo.
    *   **Pergunte explicitamente:** "Gerei o material filtrado. Há pontos que precisam de definição. Adicionei campos de `RESPOSTA:` no arquivo para facilitar. Você gostaria de responder aqui no chat ou editar o arquivo diretamente? Podemos refinar o filtro com suas respostas antes de seguir para o Canonical?"
    *   Aguarde a resolução dessas dúvidas antes de considerar o filtro concluído.