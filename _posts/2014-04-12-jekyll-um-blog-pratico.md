---
layout: post
title: "Jekyll: um blog prático"
date: "Sáb Abr 12 19:31:47 -0300 2014"
---

Sempre que alguém decide fazer um blog, a primeira plataforma que vem a cabeça é o wordpress. Comigo não foi diferente, mas estava um pouco desconfortável com a idéia por alguns motivos:

* Exagero - O Wordpress é uma plataforma robusta com muitas coisas built-in e uma infinidade de plugins para fazer virtualmente qualquer coisa (até um ecommerce). Claramente é um exagero para o blog simples que nem sei se vou postar com tanta frequencia.

+ "Hackability" - Todo mundo já ouviu alguma história desagradável de pessoas explorando alguma vulnerabilidade de uma instalação wordpress. Sempre descobrem alguma falha para te encher a paciência que, alem de ser  desagradável ter um indivíduo interferindo no seu  sistema, gera um problema de manutenção constante, que certamente é um problema para um blog sem grandes pretenções.

+ Usual - Não queria simplesmente instalar o bom e velho app do Wordpress, estava procurando algo mais divertido.

Depois de procurar um pouco encontrei o <a href="http://jekyllrb.com/" target="_blank" title="jekyll" rel="nofollow">Jekyll</a> que é um "gerador de sites estáticos" com base em textos escritos em Markdown ou Textile. Ele foi escrito em Ruby pelo Tom Preston-Warner que é um dos criadores do Github... A melhor parte dessa história é que o <a href="http://github.io/" target="_blank" rel="nofollow" title="Github pages">Github Pages</a> roda Jekyll nativamente e os caras resolveram oferecer hosting gratuito (!) para sites em Jekyll. Mão na roda, não?

Bom... Dadas as minhas premissas e essa barbada do hosting no Github não tive mais incentivo para procurar mais alternativas. Segui com o Jekyll.


##Instalando no OSX

Eu instalei o Jekyll em um Mac, mas creio que os guidelines gerais funcionariam bem para Linux. Se você usa Windows, sugiro instalar uma máquina virtual.

Segue abaixo a relação de coisas que você precisa para instalar o Jekyll:

* Xcode command line tools: Esse é só para Mac. Se você tem uma máquina da Apple baixe o Xcode ou execute no terminal: 'xcode-select --install'
* Git: É a interface de linha de comando de Git. Isso será útil para mandar o blog para o Github. Sugestão: Use homebrew para instalar.
* Rbenv: Administra suas versões de Ruby. É como o RVM só que muito mais leve e SÓ gerencia as versões instaladas e em uso de Ruby na máquina. Recomendo fortemente. Use homebrew para instalar.
* Ruby: Instale a linguagem, a versão que rodava na época desse post era a 2.1.0. Use o Rbenv para instalar
* RubyGems: Esse pacote administra as Gems de Ruby. Homebrew para instalar.
* Jekyll: Enfim o Jekyll que é uma Gem. Use o RubyGems para instalar.

Aproveitando para dar uma dica, desde que a Apple lançou o Mavericks eu tenho tido problemas para compilar algumas coisas na minha máquina, principalmente, gems como o Jekyll.O sistema retorna um erro "X-Code (ERROR: Failed to build gem native extension.". Para resolver esse erro, o primeiro passo é garantir que as command line tools estão instaladas, depois disso use essa manha para "bypassar" o problema 

~~~ bash
$ ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future gem install jekyll
~~~

Meus cumprimentos ao povo do <a href="http://stackoverflow.com/questions/22352838/ruby-gem-install-json-fails-on-mavericks-and-xcode-5-1-unknown-argument-mul" rel="nofollow" target="_blank">Stackoverflow</a>.


## Rodando o Blog

Se deu tudo certo na instalação rodar o blog deve ser bem tranquilo. É só rodar:

~~~ bash
$ jekyll new nomedoblog
$ cd nomedoblog/
$ jekyll serve
~~~

Com isso já deve começar a funcionar um template local. Em qualquer browser já estará acessível em http://localhost:4000 .

Para customizar o blog, o Jekyll tem um arquivo em YAML na raiz que é bem amigável ('_config.yml') que você pode setar diversas variáveis do blog, como o nome, título e etc.

Isso feito é só correr pro abraço e criar alguns posts. Todos eles "moram" no diretório '_posts/'. Como o Jekyll puxa "automaticamente" os posts é importante que eles sigam um padrão no nome, dessa forma eles serão identicados e disponibilizados no blog. O formato é YYYY-MM-DD-nome-do-post.markdown, sendo que a extensão do arquivo também pode ser textile.

Outra coisa importante é o "Front-Matter" do post, basicamente é um mini-YAML no começo do arquivo que passa informações relevantes como título, data do post, se ele deve ser publicado ou não, entre outras coisas.

Há algums scripts e ferramentas para facilitar essa criação de posts, por exemplo, tem gente que cria uma tarefa de Rake para gerar um post. Eu encontrei um plugin de Vim que resolve bem <a href="https://github.com/parkr/vim-jekyll" target="_blank" rel"nofollow">vim-jekyll</a>, a função mais útil é bater um ':Jpost' direto no editor para abrir um novo arquivo já no formato e com 'Front-matter' padrão.


Acho que isso é o bê-a-bá do Jekyll. Ainda tem um caminhão de customizações possíveis, mas com isso já da para rodar um blog simples.


##Servindo o Blog via Github Pages

Servir o blog via Github pages me parece uma alternativa genial. Além de ser gratuito, você não precisa se preocupar com manutenção do servidor.

Para o Github Pages funcionar você precisa criar:

* uma conta no Github, caso você não tenha (gratuita mesmo) 
* um repositório com o seguinte formato de nome: seu-username.github.io

É crucial que o nome do seu repositório seja nesse formato usando, o username do Github porque é por ele que o sistema vai identifica-lo como um blog e vai compila-lo e servi-lo.

Depois disso eu sugiro o seguinte processo:

~~~ bash
$ jekyll new seu-username.github.io
$ cd seu_username.github.io
$ git init
$ git add .
$ git commit -m 'first commit'
$ git push
~~~

Excelente, se você conseguir ver o conteúdo da pasta no seu repositório, espere uns 5-10 minutos e pode bater na URL seu-username.github.io que o blog já estará no ar.
