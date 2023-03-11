<template>
  <div>
    <h1 class="app-title">HELLO</h1>
    <img src="hudl.png" width="300" />
    <CanvasGrid :rows="rows" :columns="columns" />
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
      rows: 10,
      columns: 10,
    };
  },
};
</script>

<style scoped>
.app-title {
  font-size: 2rem;
  text-align: center;
  margin-top: 2rem;
}
</style>
