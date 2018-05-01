<template>
  <div ref="el" class="roll-carousel-host" @mouseenter="showOper=true" @mouseleave="showOper=false">
    <div class="viewport">
        <ul class="wrapper" :style="{'width':+wrapperWidth+'px','transform':'translateX('+offset+'px)'}">
            <li v-for="item in items" :key="item.key">
            <img :src="item.src" :style="{'width':+itemWidth+'px','height':+itemHeight+'px'}">
            </li>
        </ul>
    </div>
    <transition name="leftin">
        <div class="oper left" v-show="showOper" @click="prev()">
            <i class="fa fa-angle-left"></i>
        </div>
    </transition>
    <transition name="rightin">
        <div class="oper right" v-show="showOper" @click="next()">
            <i class="fa fa-angle-right"></i>
        </div>
    </transition>
  </div>
</template>
<script>
export default {
  data() {
    return {
      wrapperWidth: 0,
      offset: 0,
      itemWidth: 0,
      itemHeight: 0,
      showOper: false,
      current: 0
    };
  },
  props: ['items', 'showItemNum'],
  methods: {
    prev() {
      if (this.items.length > this.showItemNum) {
        this.current--;
        if (this.current < 0) {
          this.current = this.items.length - this.showItemNum;
        }
        this.offset = -this.current * this.itemWidth;
      }
    },
    next() {
      if (this.items.length > this.showItemNum) {
        this.current++;
        if (this.current > this.items.length - this.showItemNum) {
          this.current = 0;
        }
        this.offset = -this.current * this.itemWidth;
      }
    },
    init() {
      this.itemHeight = this.$refs.el.clientHeight;
      this.itemWidth = this.$refs.el.clientWidth / this.showItemNum;
      this.wrapperWidth = this.itemWidth * this.items.length;
    }
  },
  mounted() {
    this.init();
  }
};
</script>
<style scoped>
.roll-carousel-host {
  display: block;
  position: relative;
  margin: 0 auto;
  width: 900px;
  height: 100px;
}
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
.viewport {
  overflow: hidden;
  width: 100%;
}
.wrapper {
  transition: all 600ms;
}
.wrapper li {
  display: inline-block;
  border-top: 3px solid #000;
  cursor: pointer;
  transition: all 300ms ease;
}
.wrapper li:hover {
  border-top: 3px solid #e55137;
}
.oper {
  position: absolute;
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0.3);
  width: 30px;
  height: 30px;
  cursor: pointer;
  top: 50%;
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
.rightin-enter {
  right: -36px;
  opacity: 0;
}
.leftin-enter-to,
.rightin-enter-to,
.leftin-leave-to,
.rightin-leave-to {
  transition: all 300ms ease-in-out;
}
.leftin-leave-to {
  left: -36px;
  opacity: 0;
}
.rightin-leave-to {
  right: -36px;
  opacity: 0;
}
</style>

