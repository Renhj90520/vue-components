<template>
  <div class="hiicon-host">
      <transition name="flip" appear>
        <div class="effect" v-show="true">
            <i class="fa" :class="icon"></i>
        </div>
      </transition>
      <div class="back"></div>
  </div>
</template>
<script>
export default {
  props: ['icon']
};
</script>
<style scoped>
.hiicon-host {
  display: inline-block;
  width: 90px;
  height: 90px;
  cursor: pointer;
  border-radius: 50%;
  position: relative;
  text-align: center;
  line-height: 90px;
  font-size: 48px;
}
.back {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background-color: white;
  border-radius: 50%;
  z-index: -2;
}
.effect {
  color: #37bdb5;
  border-radius: 50%;
  box-shadow: 0 0 0 4px #37bdb5;
}
.effect::after {
  width: 100%;
  height: 100%;
  position: absolute;
  background-color: #37bdb5;
  content: '';
  top: -2px;
  left: -2px;
  border-radius: 50%;
  padding: 2px;
  box-sizing: content-box;
  transition: transform 0.2s, opacity 0.3s;
  opacity: 0;
  z-index: -1;
  transform: scale(1.3);
}
.effect:hover {
  color: white;
}
.effect:hover::after {
  opacity: 1;
  transform: scale(1);
}
.flip-enter-to {
  transition: transform 3s;
  transform: rotateY(360deg);
}
</style>
