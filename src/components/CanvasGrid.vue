<template>
  <div>
    <canvas ref="canvas" :width="canvasWidth" :height="canvasHeight" />
  </div>
</template>

<script>
export default {
  name: 'CanvasGrid',
  props: {
    element: {
      type: Object,
      default: null,
    },
    rows: {
      type: Number,
      default: 10,
    },
    columns: {
      type: Number,
      default: 10,
    },
  },
  data() {
    return {
      canvasWidth: 0,
      canvasHeight: 0,
    };
  },
  mounted() {
    const image = new Image();
    image.src = this.element.src;
    image.addEventListener('load', () => {
      this.canvasWidth = image.width;
      this.canvasHeight = image.height;
      const canvas = this.$refs.canvas;
      const context = canvas.getContext('2d');

      const cellWidth = canvas.width / this.columns;
      const cellHeight = canvas.height / this.rows;

      context.drawImage(image, 0, 0, this.canvasWidth, this.canvasHeight);

      for (let row = 0; row < this.rows; row++) {
        for (let col = 0; col < this.columns; col++) {
          const x = col * cellWidth;
          const y = row * cellHeight;

          context.strokeRect(x, y, cellWidth, cellHeight);
        }
      }
    });
  },
};
</script>

<style scoped>
canvas {
  border: 1px solid #ccc;
}
</style>