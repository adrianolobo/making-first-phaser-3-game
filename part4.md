---
title: Making your first Phaser 3 game
subtitle: Part 4 - The Platforms
date: 20th February 2018
author: Richard Davey
twitter: photonstorm
---

Adicionamos um monte de códigos à nossa função `create` que merecem uma explicação mais detalhada. Primeiro, esta parte:

```
platforms = this.physics.add.staticGroup();
```

Isso cria um novo Grupo de Física Estática e o atribui à variável local `platforms`. No Arcade Physics existem dois tipos de corpos físicos: Dinâmico e Estático. Um corpo dinâmico é aquele que pode se movimentar por meio de forças como velocidade ou aceleração. Ele pode saltar e colidir com outros objetos e essa colisão é influenciada pela massa do corpo e outros elementos.

Em contraste, um corpo estático simplesmente tem uma posição e um tamanho. Não é afetado pela gravidade, você não pode ajustar a velocidade dele e quando algo colide com ele, ele nunca se move. Estático por nome, estático por natureza. E perfeito para o chão e plataformas que vamos deixar o jogador correr por aí.

Mas o que é um grupo? Como o nome indica, são maneiras de agrupar objetos semelhantes e controlá-los como uma única unidade. Você também pode verificar a colisão entre Grupos e outros objetos do jogo. Os grupos são capazes de criar seus próprios Game Objects através de funções auxiliares como `create`. Um Grupo de Física criará automaticamente filhos habilitados para física, poupando-lhe um pouco de trabalho de braçal no processo.

Com o nosso Grupo de plataformas feito podemos usá-lo para criar as plataformas:

```
platforms.create(400, 568, 'ground').setScale(2).refreshBody();

platforms.create(600, 400, 'ground');
platforms.create(50, 250, 'ground');
platforms.create(750, 220, 'ground');
```

Como vimos anteriormente, ele cria esta cena:

No preload, importamos a imagem 'ground'. É um simples retângulo verde, com 400 x 32 pixels de tamanho e servirá para nossas necessidades básicas de plataforma:

![image](platform.png)

A primeira linha de código acima adiciona uma nova imagem ground em 400 x 568 (lembre-se, as imagens são posicionadas com base no seu centro) - o problema é que precisamos dessa plataforma para abranger toda a largura do nosso jogo, caso contrário o jogador cai dos lados. Para fazer isso nós escalamos x2 com a função `setScale(2)`. O chão agora mede 800 x 64, que é perfeito para as nossas necessidades. A chamada `refreshBody()` é necessária porque escalamos um corpo físico _estático_, então temos que dizer ao physics world sobre as mudanças que fizemos.

O chão é escalado e no lugar, então é hora das outras plataformas:

```
platforms.create(600, 400, 'ground');
platforms.create(50, 250, 'ground');
platforms.create(750, 220, 'ground');
```
O processo é exatamente o mesmo de antes, mas não precisamos escalar essas plataformas já que elas já têm o tamanho certo.

3 plataformas são colocadas ao redor da tela, separadas justamente para permitir que o jogador pule para elas.

Então vamos adicionar nosso jogador.
