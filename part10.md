---
title: Making your first Phaser 3 game
subtitle: Part 10 - Bouncing Bombs
date: 20th February 2018
author: Richard Davey
twitter: photonstorm
---

Para deixar nosso jogo mais completo, é hora de adicionar alguns vilões. Isso dará um bom elemento de desafio, algo que antes estava faltando.

A ideia é: Quando you coletar todas as estrelas pela primeira vez, será lançado uma bomba saltitante. A bomba irá saltar aleatoriamente pela fase e se você colidir com ela, você morre. Todas as estrelas irão reaparecer para que você as colete de novo, e se você o fizer, uma nova bomba será lançada. Isto irá dar ao jogador um desafio: conseguir a pontuação mais alta sem morrer.

A primeira coisa que precisamos é um Group para as bombas e alguns Colliders:

```
bombs = this.physics.add.group();

this.physics.add.collider(bombs, platforms);

this.physics.add.collider(player, bombs, hitBomb, null, this);
```

As bombar irão quicar nas plataformas, e se o player encostar nelas nós iremos chamar a função `hitBomb`. Ela irá parar o jogo e pintar o player de vermelho.

```
function hitBomb (player, bomb)
{
    this.physics.pause();

    player.setTint(0xff0000);

    player.anims.play('turn');

    gameOver = true;
}
```

Até agora tudo bem, mas nós precisamos soltar as bombas. Para fazer isto modificaremos a função `collectStar`:

```
function collectStar (player, star)
{
    star.disableBody(true, true);

    score += 10;
    scoreText.setText('Score: ' + score);

    if (stars.countActive(true) === 0)
    {
        stars.children.iterate(function (child) {

            child.enableBody(true, child.x, 0, true, true);

        });

        var x = (player.x < 400) ? Phaser.Math.Between(400, 800) : Phaser.Math.Between(0, 400);

        var bomb = bombs.create(x, 16, 'bomb');
        bomb.setBounce(1);
        bomb.setCollideWorldBounds(true);
        bomb.setVelocity(Phaser.Math.Between(-200, 200), 20);

    }
}
```

Nós utilizamos um método do Grupo chamado `countActive` para ver quantas estrelas sobraram vivas. Se não houver nenhuma, então o jogador coletou todas, então nós utilizamos a função de iterate para reativar todas as estrelas e resetar suas posições para zero. Isto falar com que todas as estrelas caiam do topo da tela de novo;

A próxima parte do código cria a bomba. Primeiro nós escolhemos uma coordenada x aleatória, sempre no lado oposto ao player, apenas para dar uma chance a ele. Então a bomba é criada, ela é configurada para colidir com o world, quicar e ter uma velocidade aleatória.

O resultado final é este pequeno sprite de bomba que salta pela tela. pequena o bastante para ser facilmente evitada, no começo, mas assim que os números aumentam começa a ficar bem difícil!

![image](part10.png)

E o nosso jogo está feito :)

### Conclusão

Você agora aprendeu como criar um sprite com propriedades físicas, controlar seu movimento e torna-lo interativo com outros objetos em um pequeno game world. Existem muitas outras coisas que você pode fazer para aperfeiçoar este jogo. Por que não expandir o tamanho da fase e permitir que a câmera role? Talvez adicionar vilões de diferentes tipos, diferentes valores, ou dar ao player uma barra de vida.

Ou para um jogo não violento, você pode torna-lo um speed-run e desafiar o jogador a coletar as estrelas o mais rápido possível.

Com o que você aprendeu neste tutorial, e as centenas de exemplos disponíveis, você deve ter agora uma fundação sólida para futuros projetos. Mas como sempre, se você tiver uma dúvida, precisar de um conselho, ou quer compartilhar o que você estrá trabalhando, então sinta-se a vontade para pedir ajuda no forum do Phaser.

### Facebook Instant Games

Phaser 3 agora tem suporte total para criar Facebook Instant Games. Agora você aprendeu como criar um jogo utilizando o Phaser, por quê não ver como é facil converte-lo em um Instant Game no nosso [Guia de primeiros passos](/tutorials/getting-started-facebook-instant-games).
