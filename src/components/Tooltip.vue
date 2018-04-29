<template>
  <div class="tooltip-host" ref="el" :class="{show:show}" :style="{left:left+'px',top:top+'px'}">
      <div class="inner">{{message}}</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      left: 0,
      top: 0
    };
  },
  props: ['message', 'show'],
  mounted() {
    const parent = this.$refs.el.parentElement;
    const parentWidth = parent.clientWidth;
    const parentHeight = parent.clientHeight;
    const selfWidth = this.$refs.el.clientWidth;
    const selfHeight = this.$refs.el.clientHeight;
    this.left = parentWidth / 2 - selfWidth / 2;
    this.top = -selfHeight;
    console.log(this.left);
    console.log(this.top);
    console.log('===================');
  }
};
</script>
<style scoped>
.tooltip-host {
  position: absolute;
  font-size: 11px;
  display: block;
  z-index: 999;
  min-width: 100px;
  opacity: 0;
  transition: all 300ms ease-in;
}
.inner {
  background-color: rgba(24, 193, 208, 0.5);
  max-width: 200px;
  padding: 3px 8px;
  color: white;
  text-align: center;
  border-radius: 4px;
  min-width: 100px;
  height: 36px;
  line-height: 30px;
}
.inner::after {
  content: ' ';
  border-width: 5px 5px 0;
  position: absolute;
  border-style: solid;
  border-color: transparent;
  border-top-color: rgba(24, 193, 208, 0.5);
  bottom: -5px;
  left: 50%;
  margin-left: -5px;
}
.show {
  opacity: 1;
}
</style>

