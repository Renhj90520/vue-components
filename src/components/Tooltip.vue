<template>
<transition name="slide">
  <div class="tooltip-host" v-show="show">
      <div class="inner">{{message}}</div>
  </div>
</transition>
</template>
<script>
export default {
  props: ['message', 'show']
};
</script>
<style scoped>
.tooltip-host {
  position: absolute;
  font-size: 11px;
  display: block;
  z-index: 999;
  top: -90%;
  min-width: 100px;
  left: -50%;
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
.slide-enter,
.slide-leave-to {
  opacity: 0;
  top: -30%;
}
.slide-enter-active,
.slide-leave-active {
  transition: all 300ms ease-in;
}
</style>

