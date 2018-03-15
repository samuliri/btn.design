<template>
  <div class="container">
    <script src="chromata.min.js"></script>
    <div>
      <img src="unnamed.jpg" id="image" class="my-image">
    </div>
    <div>
      <button id="button" class="my-button">
        <h1 class="title">
          btn
        </h1>
      </button>
      <h2 class="subtitle">
        One physical button
      </h2>
    </div>
  </div>
</template>

<script>
  if (process.browser) {
    window.onNuxtReady((app) => {

      console.log('Nuxt ready!');

      var image = document.querySelector('#image');

      var chromata = new Chromata(image, {
          pathFinderCount: 250, // 1 - 500
          speed: 8, // 1 - 20
          turningAngle: Math.PI/2, // Math.PI
          colorMode: 'greyscale', // color, greyscale
          lineWidth: 3, // 1-10
          lineMode: 'square', // smooth, square, point
          compositeOperation: 'lighten', // lighten, saturation
          origin: ['50% 50%'], // bottom, top, left, right
          outputSize: 'container', // original, container
          key: 'low', // low, high
          backgroundColor: 'hsla(34, 70%, 70%, 0)'
      });

      let btn = document.getElementById("button");
      btn.addEventListener( 'click', function (e) {
        chromata.start();
      });

      document.body.addEventListener( 'keyup', function (e) {
        if ( e.keyCode == 13 ) {
          chromata.start();
        }
      });

    })
  }
</script>

<style>
  canvas {
    cursor: none;
  }

  .my-image {
    opacity: 0;
    max-width: 100vw;
  }

  .my-button {
    margin: 15px;
    border-radius: 10px;
    cursor: help;
  }
</style>
