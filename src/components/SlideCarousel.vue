<template>
  <div class="slide-carousel-host" ref="el" @mouseenter="showOper=true" @mouseleave="showOper=false">
        <div class="viewport">
            <ul class="wrapper" :style="{'width':+wrapperWidth+'px','transform':'translateX('+offset+'px)'}">
                <li v-for="item in items" :key="item.src">
                <img :src="item.src" :style="{'width':+width+'px','height':+height+'px'}">
                </li>
            </ul>
        </div>
        <transition name="leftin">
            <div class="oper left" @click="prev()" v-show="showOper">
                <i class="fa fa-angle-left"></i>
            </div>
        </transition>
        <transition name="rightin">
            <div class="oper right" @click="next()" v-show="showOper">
                <i class="fa fa-angle-right"></i>
            </div>
        </transition>
        <ul class="indicator">
            <li v-for="(item,index) in items" @click="slideTo(index)" :class="{'active':index===current}" :key="item.src"></li>
        </ul>
  </div>
</template>
<script>
export default {
  props: ['items'],
  data() {
    return {
      wrapperWidth: 0,
      offset: 0,
      width: 0,
      height: 0,
      current: 0,
      interval: null,
      showOper: false
    };
  },
  methods: {
    init() {
      this.width = this.$refs.el.clientWidth;
      this.height = this.$refs.el.clientHeight;
      this.wrapperWidth = this.width * this.items.length;
    },
    prev() {
      this.current--;
      if (this.current < 0) {
        this.current = this.items.length - 1;
      }
      this.offset = -this.current * this.width;
    },
    next() {
      this.current++;
      if (this.current >= this.items.length) {
        this.current = 0;
      }
      this.offset = -this.current * this.width;
    },
    slideTo(index) {
      this.current = index;
      this.offset = -this.current * this.width;
    }
  },
  mounted() {
    this.init();
    this.interval = setInterval(() => {
      this.current++;
      if (this.current >= this.items.length) {
        this.current = 0;
      }
      this.offset = -this.current * this.width;
    }, 3000);
  },
  beforeDestroy() {
    if (this.interval) {
      clearInterval(this.interval);
    }
  }
};
</script>
<style scoped>
.slide-carousel-host {
  position: relative;
  margin: 0 auto;
  width: 900px;
  height: 400px;
}
.viewport {
  overflow: hidden;
}
.wrapper {
  transition: all 600ms;
}
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
li {
  display: inline-block;
  cursor: pointer;
}
.wrapper li {
  padding: 0;
  margin: 0;
}
.oper {
  position: absolute;
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0.3);
  width: 30px;
  height: 30px;
  top: 50%;
  cursor: pointer;
  text-align: center;
  line-height: 30px;
  margin-top: -15px;
  z-index: 999;
}
.oper:hover {
  background-color: rgba(0, 0, 0, 0.4);
}
.oper:hover i {
  color: #fff;
}
.oper i {
  color: rgba(255, 255, 255, 0.8);
  font-size: 20px;
  font-weight: bold;
  margin-top: 4px;
}
.left {
  left: 10px;
}
.left i {
  margin-left: -3px;
}
.right {
  right: 10px;
}
.right i {
  margin-right: -3px;
}
.leftin-enter {
  left: -36px;
  opacity: 0;
}
.leftin-enter-to,
.rightin-enter-to,
.leftin-leave-to,
.rightin-leave-to {
  transition: 300ms ease;
}
.rightin-enter {
  right: -36px;
  opacity: 0;
}
.leftin-leave-to {
  left: -36px;
  opacity: 0;
}
.rightin-leave-to {
  right: -36px;
  opacity: 0;
}
.indicator {
  width: 100%;
  text-align: center;
  position: absolute;
  display: block;
  bottom: 10px;
}
.indicator li {
  width: 8px;
  height: 8px;
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 50%;
  box-shadow: inset 0 0 3px rgba(0, 0, 0, 0.3);
  margin: 0 6px;
}
.indicator li:hover {
  background-color: rgba(0, 0, 0, 0.7);
}
.indicator li.active {
  background-color: #e55137;
  cursor: default;
}
</style>

