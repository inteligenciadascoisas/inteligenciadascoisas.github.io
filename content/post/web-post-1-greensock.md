---
layout:         post 
title:          "Animações leves e fáceis para Web"
subtitle:       "Utilizando javascript puro, imagens SVG e a biblioteca GreenSock"
description:    "Artigo e tutorial interativo sobre animações leves e fáceis para Web utilizando javascript puro, imagens SVG e a biblioteca GreenSock."
date:           2020-05-04
author:         "Alexandre Alvaro"
image:          "img/web-post-001/web-post-1-greensock.jpg"
thumbnail:      "img/web-post-001/thumb.jpg"
categories:     [ Web ]
tags:
                - web
                - tutorial
                - iniciante
                - animações
                - svg
                - javascript
                - greensock
                - interativo
---

# Introdução
Opa! Tudo belezinha?  
Este é um artigo bem interativo. Fique de olho em cada detalhe para aprender fazendo seus próprios testes! :smile:

## GIF
As animações na internet se popularizaram bastante desde o surgimento dos GIFs animados.  
O GIF é um formato de arquivo que funciona de maneira similar a um vídeo, com uma sequencia de quadros que trocam muito rapidamente gerando a ilusão de movimento.  
Cada quadro é uma imagem Bitmap (formada por pixels) e tem um máximo de 256 cores, o que deixa o arquivo leve, porém bastante limitado.  
Passe o cursor horizontalmente sobre o gif abaixo para controlar a passagem dos quadros:  
{{< gif-player "/blog/img/web-post-001/001.gif">}}

## Vetores
O uso de formas vetoriais permitiu gerar imagens escaláveis, ou seja, diferentemente dos pixels, os vetores não perdem qualidade quando redimensionados.  
Mova a barra abaixo das imagens para ver o resultado:
{{< idyll >}}
    [var name:"r" value:10 /]
    [div]
        [inline]
            [div style:`{width: '200px', height: '200px', background: '#222'}`]
                [svg width:`200` height:`200`]
                    [circle r:r cx:r cy:r fill:"#fff" /]
                [/svg]
            [/div]
        [/inline]
        [inline]
            [div style:`{width: '200px', height: '200px', background: '#222'}`]
                [div id:'circle-pixel' style:`{width: r * 2, height: r * 2}`]
                [/div]
            [/div]
        [/inline]
    [/div]
    [div style:`{width: '400px', padding: '10px 100px 10px 100px'}`]
        [Range value:r min:10 max:100 /]
    [/div]
{{< /idyll >}}

Mova os pontos azuis abaixo (ancoras) para entender melhor como as curvas são calculadas:  

{{< rawhtml >}}
    <iframe width="100%" height="400" src="https://two.js.org/examples/advanced-anchors.html" frameborder="0"></iframe>
{{< /rawhtml >}}

## SVG
Scalable Vector Graphics que pode ser traduzido do inglês como gráficos vetoriais escalonáveis. Trata-se de uma linguagem XML para descrever de forma vetorial desenhos e gráficos bidimensionais, quer de forma estática, quer dinâmica ou animada.  
No vídeo interativo: [Criando uma animação com Greensock](#criando-uma-animação-com-greensock) eu demonstro como criar um [SVG](https://www.devmedia.com.br/entendendo-e-usando-o-svg/19773) básico com algumas linhas de código.

# Principais recursos de animação para web
## Flash (atual Adobe Animate)
Por muito tempo o plugin do Flash era essencial para acessar diversas páginas. Porém, por conter falhas de segurança ele foi sendo evitado e hoje a Adobe já permite exportar as animações para um Canvas HTML5.  
Por conter um aplicativo com interface gráfica muito eficiente, é excelente para fazer animações, principalmente para uso com uma mesa digitalizadora e renderizando como vídeos, mas ainda não é minha opção preferida para rodar direto na web.  
Dá só uma relembrada nesta clássica animação sobre o Flash feita inteiramente no Flash em 2006:
{{< rawhtml >}}
    <iframe width="560" height="315" src="https://www.youtube.com/embed/Qb1VvUf21L4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{< /rawhtml >}}

## HTML5 Canvas
O HTML5 canvas tem um poder incrível e é um recurso nativo! Podendo ter os elementos acessados por WebGL é capaz de gerar gráficos complexos 2D e 3D dentro de um navegador web compatível sem o uso de plug-ins.  
Pode ser bastante interativo, usando até recursos como realidade aumentada ou mesmo um jogo completo, mas tudo fica encapsulado dentro do elemento canvas, não sendo a melhor opção para animar os demais elementos da página ([DOM](https://tableless.com.br/entendendo-o-dom-document-object-model/)).  
A capa da [página principal do blog]({{< ref "/" >}}) utiliza esse recurso :smile:, mas dependendo do conteúdo o carregamento e a execução ficam um pouco pesados.  
Até por isso resolvi não incorporar os exemplos mais legais diretamente ao artigo.  
Dá uma conferida em alguns bem legais neste link: https://www.webfx.com/blog/web-design/examples-html5-canvas/

### Three.js
Esta biblioteca JS vale ser citada! Ela permite fazer coisas inacreditáveis em conjunto com o WebGL e HTML5 Canvas.  
Dá uma conferida nos exemplos: https://threejs.org/examples/

## Animações com CSS3
Uma opção também nativa, leve e super performática, porém com opções limitadas, como curvas de movimentação (eases).  
Também não muito amigável para criar os desenhos, mas claro que sempre tem uns caras que dominam com maestria os recursos.  
Dá uma olhada no que esse brasileiro faz com CSS3 Puro:
{{< rawhtml >}}
    <iframe width="560" height="315" src="https://www.youtube.com/embed/6oRr-fvv5z4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{< /rawhtml >}}


## Javascript request animation frame
Outra opção nativa e utilizada de base por diversas bibliotecas javascript.  
Com gerenciamento de recursos adaptável ao dispositivo que está sendo utilizado, torna-se uma ótima opção, porém é muito mais fácil de implementar quando usado como recurso uma biblioteca.

## Lottie (Bodymovin’)
https://airbnb.design/lottie/  
Criado pelo time do airbnb, o Lottie é um plugin para After Effects que permite que suas animações sejam exportadas no formato JSON e lidas por um player javascript.  
Tem alguns poucos bugs e limitações, mas no geral funciona incrivelmente bem!

## Rive (Flare e 2Dimensions)
https://rive.app/  
Um pack de duas ferramentas incríveis de animação, recentemente unificada, que utliza o canvas como base e permite criar animações interativas e com recursos bem interessantes, como a deformação de meshes e esqueletos.
{{< rawhtml >}}
    <div style="display: inline-block;">
        <video class="playvideo" width="48%" height="100%" loop playsinline autoplay muted style="border-radius: 10px; " src="https://cdn.2dimensions.com/features/vertex.mp4"></video>
        <video class="playvideo" width="48%" height="100%" loop playsinline autoplay muted style="border-radius: 10px;" src="https://cdn.2dimensions.com/features/skeletal_flar4.mp4" type="video/mp4"></video>
    </div>
{{< /rawhtml >}}


A melhor opção que conheço para exportar animações para apps com Flutter.

## Web Animations API
Trata-se de um recurso javascript nativo que permite fazer sequencias complexas de animação sem precisar carregar nenhum script externo.  
Porém, além de ser bastante recente e não ter muito suporte, é bem mais limitado do que a biblioteca GASP.

## GSAP
https://greensock.com/  
Green Sock Animation Platform, é esta maravilhosa biblioteca javascript que facilita bastante a animação para web.  
Leve, modular, fácil de ler, segura e bastante robusta. E Além de tudo isso, escolhi adotar como padrão para os meus projetos pela qualidade da documentação oficial e a comunidade bastante ativa.  
Você encontra facilmente respostas bem estruturadas em fóruns, exemplos, tutoriais, vídeos e muito material bacana.  
Olha por exemplo esta ferramenta pra te auxiliar a criar as curvas de movimentação (eases):  
https://greensock.com/ease-visualizer

# Tutorial do Greensock na prática
A seguir vou demonstrar como criar uma animação básica de elementos [DOM](https://tableless.com.br/entendendo-o-dom-document-object-model/) e imagens [SVG](https://www.devmedia.com.br/entendendo-e-usando-o-svg/19773) utilizando os recursos da biblioteca GreenSock.

**O vídeo é interativo! Você pode pausar a qualquer momento, mudar o que quiser no código e ver o que acontece.**

{{< scrimba c2KvV4tN >}}

*[Clique aqui](https://www.youtube.com/watch?v=02rvd_7HcFY) para ver uma excelente explicação sobre CDN com a galera do canal Código Fonte TV.

# Considerações finais
Não existe uma unica ferramenta certa para tudo, mas pode ter certeza que pra animações interativas na web, a GASP é facilmente a minha favorita.  
Espero que tenha gostado do conteúdo e interatividade deste artigo! :blush:

Dá uma conferida nesta interface que desenhei com [SVG](https://www.devmedia.com.br/entendendo-e-usando-o-svg/19773)s feitos no Adobe Illustrator, animados com Greensock para uma aplicação interna para gestão e validação dos scripts SQL na base de teste do nosso time de desenvolvimento.  
Esta é apenas uma demonstração do FrontEnd, a solução completa foi feita em conjunto com o meu amigo [William Silva](https://github.com/Wyulliam).  

Demonstração da interatividade:  
https://alexandremendoncaalvaro.github.io/Alfred  
*Pode usar qualquer valor no usuário e senha.  

Código fonte completo do Front End disponível em Open Source:  
https://github.com/alexandremendoncaalvaro/Alfred

{{< rawhtml >}}
    <iframe width="560" height="315" src="https://www.youtube.com/embed/9q9Jo4uhZhU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{< /rawhtml >}}
