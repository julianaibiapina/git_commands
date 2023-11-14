## Sobre

No dia a dia sempre recorro ao meu caderno de anotações para relembra alguns comandos, então resolvi passar essas anotações para este arquivo e compartilhar com outras pessoas, pois pode ser útil. Essas anotações também estão disponíveis no [Notion](https://www.notion.so/Git-e-GitHub-232de171470d4f9f9e41f90f4de2153f).

⭐ Recomendo o [Visualizing Git](https://git-school.github.io/visualizing-git/) para visualização gráfia de como o git funciona.

⭐ Usarei o termo "commitar" para me referir ao ato de realizar um commit, acredito que facilite a escrita e a leitura.

## Comandos básicos

⭐`git init`: Inicializa o git no repositório em questão;

⭐ Enviar um repositório já com git para o GitHub:

1. cria um repositório no site do GitHub;
2. execurta os comandos dados pelo GitHub:

    `git remote add origin url_dada_pelo_github`

     definimos um repositório remoto dando a ele o nome de *origin* e o associamos ao que acababos de criar no GitHub.

    `git branch -m master main` altera a branch master para main no GitHub

    A partir de 1º de outubro de 2020, todos os repositórios novos que sejam criados começarão a mostrar main como ramo principal.

    `git push -u origin main`

    o `-u` significa que a partir daquele momento quando o comando `git push` for executado os códigos que estiverem na branch master serão enviados para o repositório denomidado *origin*.

⭐ `git status`: verifica em qual branch estou e se há algum arquivo (e quais) para ser commitado;

⭐ `git add`: adiciona o(s) arquivo(s) em nossa working tree.

1. `git add .`: adiciona todos os arquivos;
2. `git add nome_arquivo`: adiciona um arvivo em específico.

⭐ `git commit -m "sua_mensagem"`: o recomendado é que se faça "pequenos" commits a cada nova feature criada. Colocar uma mensagem descritiva e clara do que foi acrescentado, facilitando consultas posteriores. 

1. `git commit -m "nova mensagem" --amend`: refaz o último commit realizado acrescentando as novas modificações dos arquivos e mudando a mensagem do commit. Este comando só funciona antes de ser executado `git push`.

⭐ `git log --oneline`: retorna todo o histório de commits da aplicação e seus respectivos hashs(identificadores) apresentando-os em apenas uma linha. Para obter a versão completa remover`--oneline`.

## Lidando com branches

⭐ `git push`: coloca nossos codigos já commitados em um repositório remoto;

⭐ `git branch nome_branch`: cria uma nova branch;

⭐ `git checkout nome_branch`: muda a branch de desenvolvimento em que estamos;

⭐ `git checkout -b nome_branch`: cria uma branch e já muda para ela;

⭐ `git merge nome_branch`: une o conteúdo da branch em que estou com o conteúdo da branch que passei como parêmetro (nome_branch). Com o `merge` todos os commits que realizei na branch passada como parêmetro são acrescentados na branch de destino como um único commit;

⭐ Para acrescentar todos os commits realizados em uma branch para a branch master:

`git checkout master`

`git rebase nome_branch`

A diferença entre `merge` e `rebase` é que com este último comando todo o histórico de commits realizados na branch será acrescentado na branch master;

⭐ `git log --graph`: mostra as linhas de desenvolvimento;

## Desfazendo alterações

⭐ `git checkout -- arquivo_que_quero_reverter`: esse comando serve para desfazer alterações em arquivos ainda não adicionamos à working tree (com `git add`), ou seja, voltar à versão do último commit que executei;

⭐ `git reset HEAD nome_arquivo`: desfaz as alterações que já estão adicionamos na working tree. HEAD refere-se ao estado no qual estou trabalhando. Se `git status` for executado após esse comando, as alterações continuam nos arquivos, porém não mais marcadas para commit. Para removê-las dos arquivos basta usar o comando do item anterior;

⭐ Para desfazer alterações em arquivos que já foram commitados:

1. usar `git log --oneline` para copiar o hash do commit;

2. usar `git revert hash_do_commit` para gerar um novo commit com a remoção das alterações.

## Criando releases/versões

⭐ `git tag -a v0.1.0 -m "mensagem"`: acrescenta uma tag. As versões serão identificadas por tags. v0.1.0 é apenas um exemplo de nome e a mensagem é opcional, se não quiser colocá-la basta remover `-m "mensagem"`;

⭐ `git tag`: exibe as tags existentes;

⭐ Colocando a tag no GitHub:

1. `git push origin master`: envia nossos códigos para a branch master no repositório origin;
2. `git push origin v0.1.0`: determina que o código que está na branch master naquele momento em origin configura uma versão/release.


## Git Flow
[Fluxo de trabalho Git Flow](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)

⭐ `git flow init`: inicia as funcionalidades do git flow no repositório atual já deixando na branch develop

⭐ `git flow feature start feature_name`: inicia uma branch feature;

⭐ `git flow feature finish feature_branch`: finaliza a branch de trabalho atual e realiza o merge com a develop;

