<template>
<canvas ref="canvas" style="width:600px;height:400px;margin:20px auto;background-color:white;display:block;"></canvas>
</template>
<script>
export default {
  data() {
    return {
      source: [100, 90, 89, 123, 59]
    };
  },
  mounted() {
    const canvas = this.$refs.canvas;
    const ctx = canvas.getContext('2d');
    const width = 20;
    const currentX = 50;
    const base = 200;
    const gap = 12;
    ctx.fillStyle = 'green';
    for (let i = 0; i < this.source.length; i++) {
      const bar = this.source[i];
      ctx.fillRect(currentX + i * width + i * gap, base - bar, width, bar);
    }
  }
};
</script>

<style scoped>
</style>
