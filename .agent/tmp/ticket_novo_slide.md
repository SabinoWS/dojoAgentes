[DOJO-AGENTES] Criação de novo slide na apresentação

Link Jira: 

Razão do ticket:
- Expandir o conteúdo da apresentação do Dojo.
- Incluir novas informações relevantes para o público.
- Manter a apresentação atualizada e completa.

Definition of Done:
- Novo slide adicionado ao arquivo `slides.md`.
- Slide segue o padrão visual (Marp) dos demais.
- Conteúdo textual e visual revisado e correto.
- Slide renderiza corretamente sem quebra de layout.

História:
COMO apresentador do Dojo
QUERO adicionar um novo slide à apresentação
PARA expor um novo tópico relevante aos participantes

Cenários:
1 - Adição bem-sucedida de slide
COMO editor da apresentação
DADO QUE tenho o arquivo `slides.md` aberto
QUANDO insiro um novo bloco de slide com separador `---` e adiciono conteúdo
ENTÃO o novo slide deve aparecer na renderização final seguindo o estilo do tema

2 - Manutenção de consistência visual
COMO editor da apresentação
DADO QUE adicionei um novo slide
QUANDO visualizo a apresentação no modo slide
ENTÃO a fonte, cores e layout devem estar idênticos aos slides anteriores

Observações técnicas:
- Verificar arquivo `slides.md` na raiz.
- Utilizar sintaxe Marp.
