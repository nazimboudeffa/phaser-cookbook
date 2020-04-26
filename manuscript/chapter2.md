# Niveau 2 : Medium

Ce chapitre traitera des États, de la création d’un jeu Tilemap et d’un jeu à multiniveaux. Nous allons prendre Zelda et le jeu de Phaser CE comme exemple élémentaire.

## Qu'est-ce qu'un état

### Problème

Vous voulez définir un jeu minimal qui pourra être etendu plus tard

### Solution

Vous aurez besoin de définir un état, c'est ce à quoi il ressemble et nous utiliserons cette fonctionnalité tout au long du livre

```
var game = new Phaser.Game(640, 360);
var playState = {
  preload : function() {
    this.load.image('dude', 'assets/sprites/phaser-dude.png');
  },
  create : function(){
    this.add.image(0, 0, 'dude');
  }
};
game.state.add('play', playState);
game.state.start('play');
```

## Quelle est la meilleur manière de définir un état

### Problème

Vous avez commencé à coder avec des états et vous ne savez pas quel est le meilleur moyen de le coder

### Solution

La première méthode est celle qui utilise la méthodologie de prototypage javascript

```
var game = new Phaser.Game(800, 600, Phaser.CANVAS, 'myGame');
var myGame = {};
myGame.Play = function(game){};
myGame.Play.prototype = {
  preload: function () {
    this.load.image('dude', 'assets/sprites/phaser-dude.png');
  },
  create: function () {
    this.add.image(0, 0, 'dude');
  },
  update: function () {

  }
}
game.state.add('play', BasicGame.Play);
game.state.start('play');
```

La deuxième manière est plus codée comme dans le standard Phaser CE

```
var game = new Phaser.Game(800, 600, Phaser.CANVAS, 'myGame');

menuState = function(){
};

menuState.prototype = Object.create(menuState.prototype);
menuState.prototype.constructor = menuState;

menuState.prototype.preload = function() {
  this.load.image('dude', 'assets/sprites/phaser-dude.png');
};

playState.prototype.create = function(){
  this.add.image(0, 0, 'dude');
};??

game.state.add('menu', menuState);
game.state.start('menu');
```
