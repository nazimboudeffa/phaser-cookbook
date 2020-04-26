# Introduction

Dans ce livre je vais essayer de reprendre le framework 2D depuis le départ jusqu'à obtenir quelque chose de fonctionnel

# Chapitre 1 : Comment afficher une image en javascript

Phaser est basé sur PIXI alors essayons d'afficher une image simpele

Dans votre fichier HTML vous allez juste écrire

```
<canvas id = "canvas"></canvas>
<script>
  //code
</script>
```

Dans la partie javascript que vous allez inclure ce bout code

```
(function(){

  var canvas = document.getElementById('canvas');
  canvas.width = 400;
  canvas.height = 300;
  var context = canvas.getContext('2d');

  var image = new Image();
  image.src = 'https://raw.githubusercontent.com/nazimboudeffa/assets/master/sprites/phaser-dude.png';

  //we use an event listener to be sure that the image has been loaded
  image.addEventListener('load', function() {
    context.drawImage(image, 100, 100);
  }, false);

})();
```

Ce qu'il faut comprendre c'est que ça permet d'afficher une image avec la fonctionnel

```
drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)
```

![](images/canvas-draw-image.jpg)
