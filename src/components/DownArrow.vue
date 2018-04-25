<template>
  <div class="arrow-wrapper">
      <div class="arrow" :style="{'top':top+'px'}">
          <a href="#"></a>
      </div>
  </div>
</template>
<script>
export default {
  created() {
    this.up();
  },
  methods: {
    up() {
      this.top = 20;
      setTimeout(() => {
        this.down();
      }, 600);
    },
    down() {
      this.top = 30;
      setTimeout(() => {
        this.up();
      }, 600);
    }
  },
  data() {
    return {
      top: 30
    };
  }
};
</script>

<style scoped>
.arrow-wrapper {
  position: absolute;
  width: 80px;
  height: 80px;
  bottom: 30px;
  left: 50%;
  margin-left: -40px;
  z-index: 100;
}
.arrow {
  position: relative;
  width: 100%;
  height: 100%;
  transition: top 600ms;
}
a {
  border: 3px solid white;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  display: inline-block;
  background-color: rgba(255, 255, 255, 0.1);
  background-image: url('../assets/images/arrow.png');
  background-repeat: no-repeat;
  background-position: center;
  transition: background-color 300ms;
}
a:hover {
  background-color: #37bdb5;
}
</style>
