<template>
  <div class="container">
    <img src="test.jpg" id="image" class="my-image">
    <script src="chromata.min.js"></script>
    <script>
      var image = document.querySelector('#image');
      var chromata = new Chromata(image, {
          pathFinderCount: 60,
          speed: 9,
          turningAngle: Math.PI/2,
          colorMode: 'grescale',
          lineWidth: 4,
          lineMode: 'square',
          compositeOperation: 'saturation',
          origin: ['50% 50%'],
          outputSize: 'container', // original, container
          key: 'high',
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
