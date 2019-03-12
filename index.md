---
title: Making your first Phaser 3 game
subtitle: Part 1 - Introduction
date: 20th February 2018
author: Richard Davey
twitter: photonstorm
---

![image](tutorial_header.png)

Bem-vindo ao nosso primeiro tutorial Fazendo um jogo com Phaser 3. Nós vamos aprender como criar um pequeno jogo envolvendo um jogador correndo e pulando por plataformas, colecionando estrelas e evitando os vilões. Ao passar por este processo, vamos explicar alguns dos principais recursos do framework.

### O que é Phaser?

Phaser é um framework de jogos que visa ajudar os desenvolvedores a criarem jogos poderosos, multi-navegadores, muito rápido. Foi criado especificamente para aproveitar os benefícios dos navegadores modernos, tanto para desktop quanto para dispositivos móveis. O únicos requisito do navegador é suporte da tag canvas.

### Requisitos

[Baixe este aquivo zip](/tutorials/making-your-first-phaser-3-game/phaser3-tutorial-src.zip) que contém cada passo deste tutorial em códigos e assets que o acompanham.

Você necessita ter um conhecimento muito básico de JavaScript.

Além disso certifique-se de que você passou pelo [Guia de primeiros passos](/tutorials/getting-started), ele mostrará como fazer o download do framework, configurar um ambiente de desenvolvimento local e dará uma visão da estrutura de um projeto da Phaser e de suas principais funcionalidades. 

Se você seguiu o Guia de Introdução, você fez o download do Phaser e deixou tudo configurado e pronto para codificar. Faça o download dos assets deste tutorial e descompacte-os em sua pasta raiz da web.

Abra a página `part1.html` no seu editor preferido e vamos dar uma olhada mais de perto no código. Depois de um pequeno HTML boilerplate que inclui o Phaser, a estrutura do código se parecerá com isso:


```
var config = {
    type: Phaser.AUTO,
    width: 800,
    height: 600,
    scene: {
        preload: preload,
        create: create,
        update: update
    }
};

var game = new Phaser.Game(config);

function preload ()
{
}

function create ()
{
}

function update ()
{
}
```
O objeto *config* é por onde você configura seu jogo no Phaser. Existem muitas opções que podem ser colocadas nesse objeto e, à medida que você expande seu conhecimento sobre o Phaser, você encontrará mais delas. Mas neste tutorial vamos apenas definir o renderizador, as dimensões e uma Cena padrão.

Uma instância de um objeto Phaser.Game é atribuída a uma variável local chamada `game` e o objeto de configuração é passado para ela. Isso iniciará o processo de dar vida ao Phaser.

No Phaser 2, o objeto `game` agia como o gateway para quase todos os sistemas internos e era frequentemente acessado a partir de uma variável global. No Phaser 3, esse não é mais o caso e não é mais vantajoso armazenar a instância do jogo em uma variável global._

A propriedade `type` pode ser `Phaser.CANVAS`, `Phaser.WEBGL` ou `Phaser.AUTO`. Este é o contexto de renderização que você pode usar para o seu jogo. O valor recomendado é `Phaser.AUTO`, o qual tenta automaticamente usar o WebGL, mas se o navegador ou o dispositivo não suportar, ele voltará ao Canvas. O elemento canvas que o Phaser cria será anexado ao documento no momento em que o script foi chamado, mas você também pode especificar um contêiner pai na config do jogo, caso queira.

As propriedades `width` e `height` definem o tamanho do elemento canvas que o Phaser criará. Neste caso, 800 x 600 pixels. Seu mundo no jogo pode ser de qualquer tamanho que você quiser, mas essa é a resolução em que o jogo será exibido.

A propriedade `scene` do objeto de configuração será abordada em maiores detalhes neste tutorial.
