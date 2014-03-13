---
layout: post
title: "Configurando Twitter Cards para o seu site"
date: 2014-03-04 00:46:40 -0300
comments: true
categories: [Front-end, Semântica, HTML]
description: Provendo metainformação para o Twitter no seu site deveria você estar.
---

Quando estava configurando esse blog (em breve um post sobre) encontrei uma pequena dificuldade em fazer os [Twitter Cards](https://dev.twitter.com/cards) funcionarem corretamente. Seguindo a linha do [publique o que você aprender](http://leobetosouza.com.br/blog/2014/03/03/aprendendo-publicando-e-caminhando/), resolvi escrever um mini tutorial sobre o assunto:

<!-- more -->

## O que são Twitter Cards?

É **metainformação** que o Twitter mostra sobre um link que é colocado no tweet. Como por exemplo [nesse tweet meu](https://twitter.com/leobetosouza/status/440668936606998528):

{% img center /images/posts/2014-03-04-configurando-twitter-cards/screenshot-twitter.png [Twitter card do meu último post [screenshot do Twitter mostrando o Card gerado pelo meu último post]] %}

Se você prestar atenção verá que o Twitter além do meu tweet adicionou mais algums dados sobre o link: o titulo do artigo, o autor (eu), o nome do usuário do autor no Twitter, uma descriçao, uma foto e um link direto para o artigo.

Se você está acostumado a usar o *serviço de microblog* deve perceber que ele não gera esse tipo de dados para todos os links que são postados por lá. O motivo é que o responsável pelo site linkado tem que prover a metainformação e solicitar ao Twitter a criação dos Cards.

## Metainformação

Metainformação (ou **metadados**) são, em uma maneira bem simplista, dados sobre os dados que estão sendo transmitidos.

No caso em questão o dado é o meu post [Sobre trabalhar com o que se gosta e a falta de oportunidades](http://leobetosouza.com.br/blog/2014/03/03/sobre-trabalhar-com-que-se-gosta/) e metainformação sobre é qualquer coisa que a gente possa falar sobre ele. Como o autor, o link, quantidade de caracteres, *whatever*.

Em `HTML` a forma mais comum de adicionar metainformação à uma página é usando a tag `<meta>`.

## Twitter Cards e Open Graph

O Twitter pega a tal da metainformação da sua página se você fizer a marcação direitinho usando a sintaxe do **Open Graph**, um protocolo da **web semântica** criado pelo Facebook.

É bem simples, se você já adiciounou *markup* para o Facebook, só precisa adicionar algumas poucas *tags*.

Se você olhar o `HTML` do `<head>` do artigo acima vai achar lá essas *tags*:

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:creator" content="@leobetosouza">
<meta name="twitter:site" content="@leobetosouza">
<meta name="twitter:domain" content="leobetosouza.com.br">
<meta name="twitter:title" content="Sobre Trabalhar Com Que Se Gosta E a Falta De Oportunidades - Leobetosouza | Codando e andando">
<meta name="twitter:description" content="Uma carreira onde você não amaldiçoe a segunda-feira deveria você procurar.">
<meta property="og:image" content="http://gravatar.com/avatar/da00e54f8aa22a44d97d6dae09a8b859?size=210">
```

* `twitter:card` é o tipo de Card que você quer que o Twitter exiba. O mais comum é o `summary`, mas você pode ver os outros [nesse link](https://dev.twitter.com/docs/cards)
* `twitter:creator` é o @ do autor do artigo em questão
* `twitter:site` é o @ do seu site
* `twitter:domain` é o domínio do seu site (opcional)
* `twitter:title` o título que você quer que apareça no Card (que pode ser diferente do `<title>` da sua página)
* `twitter:descrition` um resumo de até 200 caracteres que vai aparecer no Card.
* `og:image` é a imagem que aparecerá no Card (já falo mais sobre isso)

Note que como o meu site e eu usamos a mesma conta do Twitter, então `twitter:site` e `twitter:creator` são iguais. Se você olhar [nesse artigo](http://imasters.com.br/apis/apis-paypal/testando-as-apis-paypal-no-sandbox/) do [@netojoaobatista](http://twitter.com/netojoaobatista) no [@iMasters](http://twitter.com/iMasters) vai ver um exemplo de @s diferentes.

A [Documentação](https://dev.twitter.com/docs/cards/getting-started) do Cards diz que eles aproveitam a marcação do `og:title`, `og:description` e `og:image` já usadas pelo Facebook para você não precisar adicionar as equivalentes do Twitter, mas no meu caso isso não funcionou para o título e a descrição. Eu tive que usar as *tags* do do Twitter. Por isso uso `og:image` no exemplo, mas o equivalente do Twitter é `twitter:image:src`.

## Validação e aprovação

O Twitter disponibiliza [uma ferramenta para validação e solicitação de Cards](https://dev.twitter.com/docs/cards/validation/validator) chamada *Card Validator*.

É bem fácil, só publicar sua página com a *markup* necessário, ir no *Card Validator*, clicar em *Try & Apply*, colocar o link lá e testar.

{% img center /images/posts/2014-03-04-configurando-twitter-cards/screenshot-card-validator-pendente.png [Interface do Card Validator [screenshot do Card Validator mostrando que meu card é válido e esperando aprovação]] %}

Se tiver tudo OK, vai aparecer um link para requisitar o uso do Card. Só clicar e esperar.

No meu caso eu recebi um email quase instaneamente informando o Summary Card foi ativado para o meu site:

{% img center /images/posts/2014-03-04-configurando-twitter-cards/screenshot-email.png [Email do Twitter informando que meu summary card foi aprovado [screenshot do email que o Twitter me enviou informando que ativei os summary cards para o meu site]] %}

E lá no Card Validator o status mudou :)

{% img center /images/posts/2014-03-04-configurando-twitter-cards/screenshot-card-validator-aprovado.png [Card Validator informando que meu summary card foi aprovado [screenshot do Card Validator informando que o summary card foi aprovado]] %}

Depois de tudo certo só postar seu link no Twitter e esperar que seus seguidores apreciem a novidade ;)

Se você quiser usar outro tipo de Card (como `photo` ou `summary_large_image`) no seu site, além de adicionar *markup* para o mesmo, terá que solicitar aprovação separadamente para cada um.

Espero em breve poder testar o [Product Card](https://dev.twitter.com/docs/cards/types/product-card) na [Estante Virtual](http://www.estantevirtual.com.br). ^^








