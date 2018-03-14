<template>
  <div class="container">
    <img src="unnamed.jpg" id="image" class="my-image">
    <script src="chromata.min.js"></script>
    <script>
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
      chromata.start();
    </script>
  </div>
</template>

<script>
  if (process.browser) {
    window.onNuxtReady((app) => {
      console.log('Nuxt ready!')
    })
  }
</script>

<style>
  .my-image {
    max-width: 100vw;
  }
</style>
