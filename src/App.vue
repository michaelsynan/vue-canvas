<template>
  <div id="app">
    <h1>Hello, world!</h1>

    <img :src="myimage" />

    <!---
    <CanvasGrid :element="image" :rows="10" :columns="10" />
    -->
  </div>
</template>

<script>
import CanvasGrid from './components/CanvasGrid.vue';

export default {
  name: 'App',
  components: {
    CanvasGrid,
  },
  data() {
    return {
      image: null,
      myimage: 'hudl.png',
    };
  },
  mounted() {
    const img = new Image();
    img.src = 'https://picsum.photos/id/237/200/300';
    img.onload = () => {
      this.image = img;
    };
  },
};
</script>
