<template>
  <div id="app">
    <h1>Hello, world!</h1>

    <div>
      <svg height="250" width="500" ref="myImage">
        <polygon
          points="220,10 300,210 170,250 123,234"
          style="fill: lime; stroke: purple; stroke-width: 1"
        />
        Sorry, your browser does not support inline SVG.
      </svg>
    </div>

    <CanvasGrid :element="$refs.myImage" :rows="10" :columns="10" />
  </div>
</template>

<script>
import CanvasGrid from './components/CanvasGrid.vue';

export default {
  name: 'App',
  components: {
    CanvasGrid,
  },
};
</script>
