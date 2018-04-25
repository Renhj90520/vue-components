<template>
  <div id="app">
    <app-down-arrow></app-down-arrow>
    <app-slide-menu></app-slide-menu>
  </div>
</template>

<script>
import DownArrow from './components/DownArrow';
import SlideMenu from './components/SlideMenu';
export default {
  name: 'App',
  components: {
    'app-down-arrow': DownArrow,
    'app-slide-menu': SlideMenu
  }
};
</script>

<style>
body {
  width: 100%;
  height: 100%;
  background-color: #ccc;
}
#app {
  width: 100%;
  height: 100%;
}

ul {
  list-style: none;
  padding: 0;
  clear: both;
}
</style>
