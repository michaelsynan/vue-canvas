<template>
  <div>
    <canvas ref="canvas" />
  </div>
</template>

<script>
export default {
  name: 'CanvasGrid',

  props: {
    element: {
      type: [HTMLImageElement, HTMLCanvasElement],
      required: true,
    },
    rows: {
      type: Number,
      required: true,
    },
    columns: {
      type: Number,
      required: true,
    },
  },

  mounted() {
    console.log('CanvasGrid component mounted');
    const canvas = this.$refs.canvas;
    const ctx = canvas.getContext('2d');

    // Wait for the image to load
    this.element.onload = () => {
      // Set the width and height of the canvas element to match the size of the image
      canvas.width = this.element.width;
      canvas.height = this.element.height;

      const rectWidth = canvas.width / this.columns;
      const rectHeight = canvas.height / this.rows;

      for (let row = 0; row < this.rows; row++) {
        for (let col = 0; col < this.columns; col++) {
          const x = col * rectWidth;
          const y = row * rectHeight;
          ctx.strokeRect(x, y, rectWidth, rectHeight);
        }
      }
    };
  },
};
</script>
