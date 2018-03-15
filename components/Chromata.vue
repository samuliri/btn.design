<template>
  <div class="container">
    <script src="chromata.min.js"></script>
    <div class="img-container">
      <img src="unnamed1.jpg" id="image1" class="my-image">
      <img src="unnamed2.jpg" id="image2" class="my-image" style="display:none">
      <img src="unnamed3.jpg" id="image3" class="my-image" style="display:none">
      <img src="unnamed4.jpg" id="image4" class="my-image" style="display:none">
      <img src="unnamed5.jpg" id="image5" class="my-image" style="display:none">
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

      var image1 = document.querySelector('#image1');
      var image2 = document.querySelector('#image2');
      var image3 = document.querySelector('#image3');
      var image4 = document.querySelector('#image4');
      var image5 = document.querySelector('#image5');

      var chromata1 = new Chromata(image1, {
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

      var chromata2 = new Chromata(image2, {
          pathFinderCount: 100, // 1 - 500
          speed: 8, // 1 - 20
          turningAngle: Math.PI/6, // Math.PI
          colorMode: 'greyscale', // color, greyscale
          lineWidth: 2, // 1-10
          lineMode: 'square', // smooth, square, point
          compositeOperation: 'lighten', // lighten, saturation
          origin: ['50% 50%'], // bottom, top, left, right
          outputSize: 'container', // original, container
          key: 'high', // low, high
          backgroundColor: 'hsla(34, 70%, 70%, 0)'
      });

      var chromata3 = new Chromata(image3, {
          pathFinderCount: 500, // 1 - 500
          speed: 7, // 1 - 20
          turningAngle: Math.PI/2, // Math.PI
          colorMode: 'greyscale', // color, greyscale
          lineWidth: 3, // 1-10
          lineMode: 'square', // smooth, square, point
          compositeOperation: 'lighten', // lighten, saturation
          origin: ['50% 0%'], // bottom, top, left, right
          outputSize: 'container', // original, container
          key: 'high', // low, high
          backgroundColor: 'hsla(34, 70%, 70%, 0)'
      });

      var chromata4 = new Chromata(image4, {
          pathFinderCount: 1000, // 1 - 500
          speed: 8, // 1 - 20
          turningAngle: Math.PI, // Math.PI
          colorMode: 'color', // color, greyscale
          lineWidth: 2, // 1-10
          lineMode: 'smooth', // smooth, square, point
          compositeOperation: 'lighten', // lighten, saturation
          origin: ['50% 50%'], // bottom, top, left, right
          outputSize: 'container', // original, container
          key: 'low', // low, high
          backgroundColor: 'hsla(34, 70%, 70%, 0)'
      });

      var chromata5 = new Chromata(image5, {
          pathFinderCount: 250, // 1 - 500
          speed: 8, // 1 - 20
          turningAngle: Math.PI, // Math.PI
          colorMode: 'greyscale', // color, greyscale
          lineWidth: 3, // 1-10
          lineMode: 'smooth', // smooth, square, point
          compositeOperation: 'lighten', // lighten, saturation
          origin: ['50% 50%'], // bottom, top, left, right
          outputSize: 'container', // original, container
          key: 'lighten', // low, high
          backgroundColor: 'hsla(34, 70%, 70%, 0)'
      });

      var btn = document.getElementById("button");

      btn.addEventListener( 'click', function (e) {
          event();
      });

      document.body.addEventListener( 'keyup', function (e) {
        if ( e.keyCode == 13 ) {
          event();
        }
      });

      var start = 0;
      var i = 1;
      var current = "";

      function event() {
        if(start == 0) {
          if(current == chromata5) {
            current.reset();
            document.getElementById("image5").style.display = "none";
          }
          chromata1.start();
          start = 1;
        } else {
          current = eval(" chromata"+i);
          current.reset();
          document.getElementById("image"+i).style.display = "none";
          i++;
          var next = eval(" chromata"+i);
          next.start();
        }
        if(i==5) {
          current = eval(" chromata"+i);
          start = 0;
          i = 1;
        }
      }

    })
  }
</script>

<style>
  .img-container {
    width: 100vw;
  }

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
