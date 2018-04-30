<template>
    <div class="galleryitem-host" >
        <img :src="img.src">
        <transition name="bounce">
          <div class="mask" v-show="showMask"></div>
        </transition>
        <div class="content" @mouseenter="show" @mouseleave="hide">
            <transition name="slide">
              <h2 v-show="showTitle">{{img.title}}</h2>
            </transition>
            <transition name="slide">
              <p v-show="showDesc">{{img.description}}</p>
            </transition>
            <transition name="slide">
              <a class="more" v-show="showMore" href>Read More</a>
            </transition>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      showMask: false,
      showTitle: false,
      showDesc: false,
      showMore: false
    };
  },
  props: ['img'],
  methods: {
    show: function() {
      this.showMask = true;
      this.showMore = true;
      setTimeout(() => {
        this.showTitle = true;
      }, 400);
      setTimeout(() => {
        this.showDesc = true;
      }, 200);
    },
    hide: function() {
      this.showMask = false;
      setTimeout(() => {
        this.showMore = false;
      }, 300);
      setTimeout(() => {
        this.showDesc = false;
      }, 200);
      setTimeout(() => {
        this.showTitle = false;
      }, 100);
    }
  }
};
</script>
<style scoped>
.galleryitem-host {
  display: inline-block;
  width: 320px;
  height: 220px;
  border: 10px solid #fff;
  box-shadow: 1px 1px 2px #e6e6e6;
  position: relative;
  overflow: hidden;
  text-align: center;
}
img {
  display: block;
  position: relative;
  min-width: 300px;
  min-height: 200px;
  max-width: 400px;
  max-height: 300px;
}
.mask {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 0.7);
}
.content {
  position: absolute;
  top: 0;
  left: 0;
  width: 300px;
  cursor: pointer;
  height: 200px;
}

h2 {
  position: relative;
  text-align: center;
  background-color: rgba(0, 0, 0, 0.8);
  color: white;
  font-size: 17px;
  font-weight: bold;
  padding: 10px;
  margin-top: 20px;
  line-height: 40px;
  transform: translateY(0px);
}
p {
  color: #333;
  text-align: center;
  font-style: italic;
  padding: 10px 20px 20px;
  font-size: 12px;
  transform: translateY(0px);
}
.more {
  display: inline-block;
  text-decoration: none;
  padding: 7px 14px;
  background-color: #000;
  color: #fff;
  box-shadow: 0 0 1px #000;
  transform: translateY(0px);
}
.more:hover {
  box-shadow: 0 0 5px #000;
}
.bounce-enter {
  transform: translateY(-200px);
}
.bounce-enter-to {
  animation: bounce-down 900ms;
}
.bounce-leave {
  transform: translateY(0px);
}
.bounce-leave-to {
  transform: translateY(-200px);
  transition: transform 300ms 500ms ease-out;
}
.slide-enter,
.slide-leave-to {
  transform: translateY(-200px);
}
.slide-enter-to {
  transition: transform 200ms ease-in;
}
.slide-leave-to {
  transition: transform 200ms ease-in-out;
}
@keyframes bounce-down {
  0% {
    transform: translateY(-205px);
  }
  40% {
    transform: translateY(-100px);
  }
  55% {
    transform: translateY(0px);
  }
  65% {
    transform: translateY(-52px);
  }
  75% {
    transform: translateY(0px);
  }
  82% {
    transform: translateY(-25px);
  }
  87% {
    transform: translateY(0px);
  }
  92% {
    transform: translateY(-12px);
  }
  97% {
    transform: translateY(0px);
  }
  100% {
    transform: translateY(100%);
  }
}
</style>
