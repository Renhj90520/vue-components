<template>
    <div class="slide-container" :style="{'left':left+'px'}">
        <div class="slide-content">
            <p>Colors -
            <i style="font-size:11px;"> * You can use Unlimited Colors</i>
            </p>
            <ul class="clearfix">
            <li>
                <a href="#" class="color cyan"></a>
            </li>
            <li>
                <a href="#" class="color carrot"></a>
            </li>
            <li>
                <a href="#" class="color pink"></a>
            </li>
            <li>
                <a href="#" class="color green"></a>
            </li>
            <li>
                <a href="#" class="color red"></a>
            </li>
            <li>
                <a href="#" class="color blue"></a>
            </li>
            <li>
                <a href="#" class="color purple"></a>
            </li>
            <li>
                <a href="#" class="color yellow"></a>
            </li>
            </ul>
            <p>Template Style</p>
            <p class="flx-slect-layout">
                <input type="radio" checked="checked" id="light">
                <label for="light">Light</label>
                <input type="radio" checked="checked" id="dark">
                <label for="dark">Dark</label>
            </p>
        </div>
        <a class="toggle-btn" @click="toggleMenu()"></a>
    </div>
</template>
<script>
export default {
  data() {
    return {
      isShow: false
    };
  },
  methods: {
    toggleMenu() {
      this.isShow = !this.isShow;
    }
  },
  computed: {
    left() {
      return this.isShow ? 0 : -308;
    }
  }
};
</script>
<style scoped>
.slide-container {
  display: flex;
  position: fixed;
  top: 100px;
  z-index: 99999;
  color: #3d3d3d;
  transition: left 300ms ease-in-out;
}
.slide-content {
  width: 308px;
  background-color: white;
}

li {
  float: left;
  margin: 0 1px 1px 0;
}

li a {
  display: block;
  width: 32px;
  height: 32px;
  background-size: 0 0;
  background-image: url('../assets/images/switch-color-active.png');
  background-position: center center;
  background-repeat: no-repeat;
  background-color: #ccc;
  border-radius: 50%;
  opacity: 1;
  transition: all 0.3s ease-in-out;
}
.color.carrot {
  background-color: #e77874 !important;
}

.color.cyan {
  background-color: #37bdb5 !important;
}

.color.pink {
  background-color: #ec6197 !important;
}

.color.green {
  background-color: #89b424 !important;
}

.color.red {
  background-color: #d44646 !important;
}

.color.blue {
  background-color: #3498db !important;
}

.color.purple {
  background-color: #8e44ad !important;
}

.color.yellow {
  background-color: #f1c40f !important;
}

li a:hover,
li a:active {
  background-size: 10px 10px;
  opacity: 0.5;
}
.toggle-btn {
  width: 30px;
  height: 40px;
  background-image: url('../assets/images/setting.png');
  background-repeat: no-repeat;
  background-position: center;
  background-color: white;
  border: 1px solid #f0f0f0;
  border-radius: 0 2px 2px 0;
  margin-left: -1px;
  border-left: 0;
  cursor: pointer;
}
.slide-enter {
  left: -308px;
}
.slide-enter-active {
  transition: all 1s ease-in-out;
  left: 0;
}
.slide-leave {
  left: -308px;
}
.slide-leave-active {
  transition: all 1s ease-in-out;
}
</style>
