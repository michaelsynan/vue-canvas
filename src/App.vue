<template>
  <div>
    <CanvasCols
      :image="theimage"
      :columns="columns"
      :rows="rows"
      :canvasHeight="100"
    />
  </div>
</template>

<script>
import { ref } from 'vue';
import CanvasCols from '@/components/CanvasCols.vue';

export default {
  components: {
    CanvasCols,
  },
  setup() {
    const theimage = ref('/logo.png');
    const columns = ref(8);
    const rows = ref(8);

    return {
      theimage,
      columns,
      rows,
    };
  },
};
</script>
