<template>
<div id="app">
  <div class="space">
    <app-down-arrow></app-down-arrow>
    <app-slide-menu></app-slide-menu>
  </div>
  <div class="container">
    <app-timeline></app-timeline>
  </div>
</div>
</template>

<script>
import DownArrow from './components/DownArrow';
import SlideMenu from './components/SlideMenu';
import Timeline from './components/Timeline';
export default {
  name: 'App',
  components: {
    'app-down-arrow': DownArrow,
    'app-slide-menu': SlideMenu,
    'app-timeline': Timeline
  }
};
</script>

<style>
html {
  width: 100%;
  height: 100%;
}
body {
  width: 100%;
  height: 100%;
  background-color: #ccc;
}
#app {
  height: 100%;
}
.space {
  width: 100%;
  height: 100%;
  margin-bottom: 20px;
}

ul {
  list-style: none;
  padding: 0;
  clear: both;
}
.whiteback {
  background-color: white;
}
</style>
