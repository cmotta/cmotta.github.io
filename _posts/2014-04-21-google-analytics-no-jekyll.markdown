---
layout: post
title: "Google Analytics no Jekyll"
date: "Seg Abr 21 18:31:37 -0300 2014"
---

Colocar um blog do ar é legal e etc. Mas você não tem muita visibilidade sobre o que está acontecendo, quem está visitando, o que as pessoas estão vendo, enfim...

Uma forma rápida de colher informações é incluir o rastreamento do Google Analytics.

O rastreamento é feito via um código javascript que você inclui no seu site. Esse código envia dados para o Google todas as vezes que é ativado, usualmente, por uma visita de um usuário na página.


##Criando uma Conta do Google Analytics

Para fazer isso funcionar, você precisa criar uma conta gratuita no <a href='http://analytics.google.com' title='Google Analytics' rel='nofollow'>Google Analytics</a>.

Basicamente, faça o login e clique em criar conta. Na época que criei esse post você ainda podia criar uma 'conta clássica', mas sugiro selecionar o 'Universal Analytics' já que o Google está migrando gradualmente todas as contas para esse padrão.

De forma geral, está pronto. Você já terá um código do Analytics para inserir no site. 

Algumas outras coisas que sugiro ativar:

1. Relatórios de demografia e interesses: Apesar de ser bem geral, essa feature do Analytics te ajuda a entender um pouco mais sobre os visitantes do seu site
2. Atribuição avançada de cliques: Esse 'código extra' ajuda você a entender onde o usuário está realmente clicando. Se você tem links duplicados na sua página é essencial ter esse parâmetro ativo.
3. Ligação com o <a href='http://www.google.com/webmasters/' rel='nofollow' title='Webmasters - Google'> Webmaster Tools</a>: Essa ferramenta é bem importante para te ajudar a entender como o Google está rastreando o seu site e classificando-o na busca orgânica do Google (!!!).

Todas essas mudanças podem ser feitas na seção admin do Analytics dentro de 'configurações da propriedade' (property settings).

Lembre-se: você só deve copiar o código javascript depois que tiver feito as mudanças de configuração.

No final, seu código deveria se parecer com este:

``` javascript
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-XXXXXXX-Y', 'nomedoseublog');
  ga('send', 'pageview');

</script>

```


##Instalando no Jekyll

Para colocar isso no Blog, você precisa 'chamar' esse código no final da tag `<head>` de todas as suas páginas. Se você instalou a versão básica do Jekyll, você deve incluir isso dentro de `_layouts/default.html`.

Ficará parecido com isso:

``` html
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <title>{{ page.title }}</title>
  <meta name="viewport" content="width=device-width">

  <!-- syntax highlighting CSS -->
  <link rel="stylesheet" href="/css/syntax.css">
  <!-- Custom CSS -->
  <link rel="stylesheet" href="/css/main.css">

  {% include _google-analytics.html %}

</head>
```


##Como eu testo se funciona?

Meu jeito preferido de testar se o Analytics está funcional é olhando a aba 'Realtime'.

Quando você estiver nessa aba, acesse seu blog normalmente, pode ser na home mesmo. Em instantes, você vai conseguir enxergar um 'hit' no analytics:

![Testando o Google Analytics](/assets/media/testando-google-analytics.png)

Boa! Se está aparencendo no Analytics o Google cuida do resto. Aproveite.
