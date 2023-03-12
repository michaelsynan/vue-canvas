<template>
  <div>
    <h1 class="app-title">Canvas Example</h1>
    <div class="columns-container">
      <div
        v-for="(column, index) in columns"
        :key="index"
        :id="'column-' + index"
        class="column"
        :style="{ width: columnWidth + 'px' }"
      >
        <canvas
          :ref="'canvas-' + index"
          :width="columnWidth"
          :height="canvasHeight"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      canvasWidth: 0,
      canvasHeight: 0,
      columns: 5,
      columnWidth: 0,
    };
  },
  mounted() {
    const image = new Image();
    image.src = '/hudl.png';
    image.addEventListener('load', () => {
      this.canvasWidth = image.width;
      this.canvasHeight = image.height;
      this.columnWidth = this.canvasWidth / this.columns;

      const columnImages = [];
      for (let i = 0; i < this.columns; i++) {
        columnImages[i] = new Image();
        columnImages[i].src = '/hudl.png';
        columnImages[i].addEventListener('load', () => {
          const canvas = this.$refs['canvas-' + i][0];
          const context = canvas.getContext('2d');
          context.drawImage(
            columnImages[i],
            i * this.columnWidth,
            0,
            this.columnWidth,
            this.canvasHeight,
            0,
            0,
            this.columnWidth,
            this.canvasHeight
          );
        });
      }
    });
  },
};
</script>

<style scoped>
.app-title {
  font-size: 2rem;
  text-align: center;
  margin-top: 2rem;
}

.columns-container {
  display: flex;
}

.column {
  display: flex;
  justify-content: center;
  align-items: center;
}

#column-1 {
  margin-top: 20px;
}
#column-3 {
  margin-top: 20px;
}
#column-5 {
  margin-top: 20px;
}
#column-7 {
  margin-top: 20px;
}
</style>
