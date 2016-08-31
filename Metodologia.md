Projeto & Desenvolvimento de Sistemas de Informação

##Metodologia para equipe distribuída

###Resumo Executivo

Este guia descreve um [método de gerenciamento de fontes ](http://en.wikipedia.org/wiki/Revision_control "Revision control") que auxilia equipes de Projeto & Desenvolvimento (P&D) envolvidas na criação e construção de Sistemas de Informação (SI). O método combina conceitos e ferramentas que permitem à equipe focar em sua missão, mesmo com participantes distribuídos geograficamente e no tempo.

A figura abaixo apresenta as camadas que compõe um `Produto/Projeto`. A decomposição em `Releases` permite estabelecer metas intermediárias, agregando valor incremental ao processo de melhora contínua. O dia a dia da equipe é planejado e executado de forma iterativa, através de grande quantidade de `Stories` agrupadas em unidades de trabalho denominadas `Sprints`.   

![User Story Mapping](http://i.imgur.com/7NzyIrH.png)

São relacionados inicialmente uma série de conceitos e ferramentas, com links, para os quais recomenda-se atenção prévia.

- O [Sprint](http://en.wikipedia.org/wiki/Scrum_(software_development)#Sprint "Scrum Sprint") mede a unidade de trabalho que incrementa a evolução da equipe na execução da missão;
- Cada Sprint é composto por múltiplas tarefas ou [estórias](http://www.agilemodeling.com/artifacts/userStory.htm "Introduction to User Stories"), utilizando a técnica de [User Story Mapping](http://jpattonassociates.com/wp-content/uploads/2015/01/how_you_slice_it.pdf "User Story Mapping");
- As estórias podem ser reorganizadas em [mapas](http://www.agileproductdesign.com/blog/the_new_backlog.html "The new user story backlog is a map") que são atualizados automaticamente;
- São utilizadas as ferramentas [Pivotal Tracker](https://www.pivotaltracker.com "Tracker") para gerenciar as estórias e [GitHub](https://github.com/features "GitHub") para armazenar o repositório de dados;
- O método permite que o estado da estória [evolua à cada mudança](http://pivotallabs.com/github-service-hook-for-pivotal-tracker/ "Github service hook for Pivotal Tracker") introduzida pela equipe P&D no repositório de dados.
- Uma combinação do [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html "Descrição GitHub Flow") e do [Simple git branching model](https://gist.github.com/jbenet/ee6c9ac48068889b0912 "by jbenet") ordena a atualização do repositório pela equipe P&D, resolvendo conflitos inerentes ao acesso concorrente a um repositório de dados comum;
- O [Pivotal Tracker é uma ferramenta de gerenciamento](http://www.slideshare.net/danpivotal/pivotal-tracker-overview "Pivotal Tracker Overview") que mantem a equipe focada em fazer acontecer, dentro das prioridades combinadas. Sua [utilização de forma efetiva](http://www.rixiform.com/2010/06/01/using-pivotal-tracker-effectively/ "Using Pivotal Tracker Effectively") ajuda cada membro da equipe a responder à pergunta: "Em que eu devo trabalhar a seguir?" Ajuda também a estimar prazos futuros, baseando-se no trabalho realizado pela equipe no passado.

###Sprint

[Sprint](http://en.wikipedia.org/wiki/Scrum_(software_development)#Sprint "Scrum Sprint") is a term used in Scrum agile project management methodology. A sprint (or iteration) is the basic unit of development, treated as a "timeboxed" effort, and restricted to a specific duration. The duration is fixed in advance for each sprint and is normally between one week and one month, although two weeks is typical.

Each sprint is started by a planning meeting, where the tasks for the sprint are identified and an estimated commitment for the sprint goal is made, and ended by a sprint review-and-retrospective meeting, where the progress is reviewed and lessons for the next sprint are identified.

![Sprint](http://i.imgur.com/dwIhZ0h.png)

###Branching Model

Como veremos adiante, cada mudança inicia com o repositório sendo replicado. Através de um `branch-de-mudança`, é criada uma área privativa no repositório para se armazenar a mudança. Isto permite que os membros da equipe trabalhem sem interferência mútua. O `branch-master` é preservado até que um membro da equipe submeta um `branch-de-mudança` para revisão e aprovação. Neste momento, um membro `revisor` da equipe deverá auditar o trabalho realizado e realizar o merge do `branch-de-mudança` com o `branch-master`.

Com isso, as contribuições publicadas no `branch-de-mudança` são propagadas para o `branch-master`, ou seja, incorporadas definitivamente ao repositório de dados. A partir daí, todos os membros da equipe podem se atualizar com a mudança e consultar as alterações do repositório.

O método utiliza o [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html "Descrição GitHub Flow") para ordenar a atualização do repositório pela equipe de P&D. O método também foi influenciado pelas operações de `git rebase` publicadas em [A simple git branching model](https://gist.github.com/jbenet/ee6c9ac48068889b0912 "by jbenet").

###GitHub Flow

A seguir informações sobre o workflow **GitHub Flow**, a partir de seus próprios criadores.

> So, what is [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html "Detalhes de GitHub Flow")?
> 
> - Anything in the master branch is deployable
> To work on something new, **create a descriptively named branch** off of master****;
> - **Commit to that branch** locally and regularly push your work to the same named branch on the server;
> - When you need feedback or help, or you think the branch is ready for merging, **open a pull request**;
> - After someone else has reviewed and signed off on the feature, you can **merge it into master**;
> - Once it is merged and pushed to ‘master’, you can and should deploy immediately;
 
> That is the entire flow. It is very simple, very effective and works for fairly large teams – GitHub is 35 employees now, maybe 15-20 of whom work on the same project (github.com) at the same time. I think that most development teams – groups that work on the same logical code at the same time which could produce conflicts – are around this size or smaller. Especially those that are progressive enough to be doing rapid and consistent deployments.

> Some [tricks](https://github.com/blog/1124-how-we-use-pull-requests-to-build-github "How we use Pull Requests to build GitHub") to make Pull Requests more awesome for your project:
> 
> - Open a Pull Request as early as possible: Pull Requests are a great way to start a conversation of a feature, so start one as soon as possible - even before you are finished. Your team can comment on the feature as it evolves, instead of providing all their feedback at the very end.
> - Pull Requests work branch to branch: No one has a fork of github/github. We make Pull Requests in the same repository by opening Pull Requests for branches.
> - A Pull Request doesn't have to be merged: Pull Requests are easy to make and a great way to get feedback and track progress on a branch. But some ideas don't make it. It's okay to close a Pull Request without merging; we do it all the time.

###Story

Cada estória deve se enquadrar no formato:

	    as a (role)
	    I want to (do something)
	    In order to (benefit)

Os estados de uma estória são listados a seguir, com uma descrição sucinta:

> - **not yet started:** estado inicial, antes da estória começar.
> - **started:** estória começa, clicando-se no botão start no PT;
> - **finished:** sincronizada pelo commit no repositório, quando a tarefa é concluída;
> - **delivered:** quando as alterações são publicadas no staging server;
> - **accepted:** quando as alterações são aceitas;
> - **rejected:** em caso de rejeição depois de publicadas.

###Workflow da mudança

O diagrama abaixo resume os passos necessários para se efetuar uma mudança:

![Workflow da mudança](http://i.imgur.com/u6pDNDi.png)


- **Clonar repositório local de trabalho.** Convencionando-se que os repositórios locais de trabalho em cada micro virtual ficarão armazenados a partir de `c:\_git`, abrir shell (janela para comandos) , clicando-se o botão direito do mouse e selecionando `git bash here`. Para se clonar o fork de um desenvolvedor, utiliza-se o comando abaixo, conforme exemplo mostrado a seguir:

		> git clone git@github.com:josemotta/CameraMan.git

	![Clonar repositório](http://i.imgur.com/NLBpIGG.png)

	Em seguida, o comando `cd cameraman` poderia ser usado para se chegar ao  repositório local de trabalho. Outra alternativa seria abrir um novo shell, clicando-se o botão direito do mouse no folder `c:\_git\CameraMan` de seu micro virtual e selecionado-se git bash here, conforme mostrado a seguir.

	![Git Bash Here](http://i.imgur.com/oViLBem.png)

- **Clicar 'start' na estória do PT.** Isso dará início à uma estória do PT. Favor reparar que cada estória tem um id de identificação, assinalado na figura abaixo, que deverá ser aplicado nos comentários dos commits realizados pela equipe P&D, conforme veremos mais adiante.

	![Story ID](http://i.imgur.com/LyRM1Ly.png)

- **Cria-se o branch `change-name`.** Voltando ao repositório, a partir do branch `master`, cria-se um novo branch `change-name` que vai abrigar a mudança que o membro da equipe P&D irá realizar. O nome do branch deve ser escolhido de forma cuidadosa, refletindo sucintamente a estória/tarefa a ser realizada. Veja um exemplo:

    	git checkout -b change-name

	![Criar branch para mudança](http://i.imgur.com/HS7glCr.png)

	Em hipótese alguma o branch `master` deverá ser diretamente alterado. A  integridade do repositório principal se baseia no fato que as mudanças serão sempre introduzidas, de forma assíncrona, pelo branch `change-name` criado exclusivamente com essa finalidade. Alterações no branch `master` são somente realizadas pelo merge com um branch `change-name`.

- **Efetuar a mudança.** Fazer as alterações relativas à estória no repositório local.

- **Salvar a mudança.** Cada mudança corresponderá a um comando commit que incluirá o `id` da estória do PT. O  formato do commit é mostrado a seguir:

	`[#12345678] Incluir um comentário pertinente ao commit`

	Veja a seguir a lista completa dos comandos a serem executados para salvar as mudanças no branch `change-name`. A mudança é salva no repositório local e em seguida propagada para o branch de mesmo nome (`change-name`) no repositório principal do projeto:
    
    	git add .
    	git commit -am "[#12345678] Comentário para histórico do projeto"
	    git push origin change-name

-	**Repetir ciclo.** O desenvolvedor repetirá esse ciclo quantas vezes for necessário. A inclusão do `id` da estória no  `commit` é fundamental para que seja adicionado um link ao campo `Activity` da estória do PT, conforme pode ser visto a seguir.

	![Integração PT GitHub](http://i.imgur.com/Y0RlxRR.png)

	Clicando-se esse link, todos podem acompanhar as alterações introduzidas no repositório em cada mudança. O último commit, quando o desenvolvedor da equipe P&D julgar que a tarefa terminou, deverá incluir a palavra `finish` após o `id` da estória, conforme mostrado  abaixo. Desta forma, o estado da estória no PT será automaticamente evoluída.

	    git add .
	    commit -am "[#12345678 finish] Histórico finalizando a estória"
	    git push origin change-name

    
- **Solicitar um pull request.** Em seguida, o desenvolvedor vai ao site do GitHub e solicita um `pull request` do branch `change-name`. A partir daí, será iniciado um diálogo entre os membros da equipe visando a aceitação ou rejeição das mudanças introduzidas no branch `change-name`. O site Github possui facilidades para permitir que a equipe discuta a aceitação das mudanças.

    **A Pull Request doesn't have to be merged**: Pull Requests are easy to make and a great way to get feedback and track progress on a branch. But some ideas don't make it. It's okay to close a Pull Request without merging; we do it all the time.


- **Merge das alterações.** Deverão ser publicadas as alterações no repositório `master` do projeto. 


- **Aceitar/rejeitar as alterações no projeto.** Por final, quando a estória for auditada no staging server ela poderá ser aceita para publicação final no site de produção. Em ambos os casos (estória aceita/rejeitada), o branch `change-name` correspondente deverá ser removido ao final do ciclo da mudança.

##Sessão exemplo

No exemplo abaixo, inicia-se uma sessão atualizando o `master local`, a partir do `origin`, ou seja, o repositório   git@github.com:trendnet/lab.git na Internet. Em seguida, nos deslocamos para o `branch news1` com o comando `git checkout news1` e verificamos que o mesmo está sincronizado com o repositório da Internet.

Neste ponto, o usuário realiza uma alteração no repositório. No final, pretende seguir os procedimentos para atualizar o repositório. Inicia com o comando `git add .`, seguido do `git commit -am "[#63657130] add Treinamentos no Brasil"`. Repare que foi incluído o `id` da estória, no formato `[#63657130]`. Como há integração entre os sites github.com e pivotaltracker.com, será registrada esta alteração no repositório para toda a equipe.

O comando `git push origin news1` atualiza o `branch news1` na Internet. Vamos agora transferir esta modificação para o repositório principal, começando com o deslocamento para o `master`, através do comando `git checkout master`. Faz-se então o merge, com `git merge --no-ff news1`. Em seguida, atualiza-se o `master` na Internet, de forma que todos da equipe tenham acesso às modificações.

![Sessão exemplo](http://i.imgur.com/opXkMbd.png)

##Setup

Passos iniciais para se utilizar este método:

- criar projeto no site Pivotal Tracker (PT);
- criar repositório no GitHub;
- incluir arquivo .gitconfig contendo `git config --global branch.autosetuprebase always`;
- incluir arquivo .gitignore adequado ao projeto
- configurar integração do site GitHub com Hook para Pivotal Tracker no repositório;
- treinar equipe P&D nas ferramentas usadas no método;
- iniciar o processo, seguindo-se o workflow do projeto.

###Integração Github com Pivotal Tracker

> [SCM Post-Commit Hook Overview](http://www.pivotaltracker.com/help/api?version=v3#scm_post_commit "SCM Post-Commit Hook Overview")
> 
> 
> The Tracker API supports integration with post-commit hooks of Source Control Management (SCM) systems such as Subversion, Git, etc. When a commit is made to the SCM, a trigger can call the Tracker API to add a story comment with the commit ID, author and message. It can also optionally change story state. 

A integração [Pivotal Tracker com GitHub](http://pivotallabs.com/github-service-hook-for-pivotal-tracker/ "configuração") tem dupla função: registrar o andamento das estórias e alterar o seu estado. As [atualizações](http://www.pivotaltracker.com/help/api?version=v3#scm_post_commit "operação") são realizadas sincronamente nos repositórios, pois o Github aciona o Pivotal Tracker para evoluir uma estória, por exemplo de "Started" para "Finished".