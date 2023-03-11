<template>
  <canvas ref="canvas" />
</template>

<script>
export default {
  name: 'CanvasGrid',
  props: {
    rows: {
      type: Number,
      default: 10,
    },
    columns: {
      type: Number,
      default: 10,
    },
  },
  mounted() {
    const canvas = this.$refs.canvas;
    const context = canvas.getContext('2d');

    const cellWidth = canvas.width / this.columns;
    const cellHeight = canvas.height / this.rows;

    for (let row = 0; row < this.rows; row++) {
      for (let col = 0; col < this.columns; col++) {
        const x = col * cellWidth;
        const y = row * cellHeight;

        context.strokeRect(x, y, cellWidth, cellHeight);
      }
    }
  },
};
</script>

<style scoped>
canvas {
  border: 1px solid #ccc;
}
</style>
