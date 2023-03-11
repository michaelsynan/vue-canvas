<template>
  <div>
    <canvas ref="myCanvas" />
  </div>
</template>

<script>
export default {
  name: 'CanvasGrid',

  props: {
    element: {
      type: [HTMLImageElement, HTMLCanvasElement, SVGElement], // add SVGElement to the type
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
    const canvas = this.$refs.myCanvas;
    const ctx = canvas.getContext('2d');
    const svg = this.element.cloneNode(true);

    // Create a temporary SVG element to calculate the actual dimensions of the SVG
    const svgWrapper = document.createElement('div');
    svgWrapper.appendChild(svg);
    document.body.appendChild(svgWrapper);

    const rect = svg.getBoundingClientRect();
    canvas.width = rect.width;
    canvas.height = rect.height;

    document.body.removeChild(svgWrapper);

    const rectWidth = canvas.width / this.columns;
    const rectHeight = canvas.height / this.rows;

    for (let row = 0; row < this.rows; row++) {
      for (let col = 0; col < this.columns; col++) {
        const x = col * rectWidth;
        const y = row * rectHeight;
        ctx.strokeRect(x, y, rectWidth, rectHeight);
      }
    }
  },
};
</script>
