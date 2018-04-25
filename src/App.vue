<template>
  <div id="app">
    <app-down-arrow></app-down-arrow>
  </div>
</template>

<script>
import DownArrow from './components/DownArrow';
export default {
  name: 'App',
  components: { 'app-down-arrow': DownArrow }
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
</style>
