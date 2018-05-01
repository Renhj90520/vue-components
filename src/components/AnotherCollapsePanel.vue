<template>
  <div class="collapse-host" ref="el">
        <a class="title" @click="toggleState()">
            <i class="fa" :class="{'fa-plus':!state,'fa-minus':state}"></i>
            <span>{{title}}</span>
        </a>
        <div class="content" :class="{'open':state}" :style="{'margin-top':margin+'px'}">
            <slot></slot>
        </div>
  </div>
</template>
<script>
export default {
  props: ['title'],
  data() {
    return {
      state: false,
      margin: 0,
      clientHeight: 0
    };
  },
  methods: {
    toggleState() {
      this.state = !this.state;
      if (this.state) {
        this.margin = 0;
      } else {
        this.margin = -this.clientHeight;
      }
    }
  },
  mounted() {
    this.clientHeight = this.$refs.el.clientHeight;
    this.margin = -this.clientHeight;
  }
};
</script>
<style scoped>
.collapse-host {
  position: relative;
  height: auto;
  min-height: 40px;
}
a {
  text-decoration: none;
  cursor: pointer;
}
.title {
  line-height: 40px;
  display: block;
  color: #fff !important;
  background-color: #111;
  padding-left: 10px;
  transition: all 300ms ease-in-out;
}
.title i {
  font-size: 16px;
}
.title span {
  font-size: 16px;
  margin-left: 10px;
}
.title:hover {
  background-color: #07bfca;
}
.content {
  padding: 20px;
  background-color: #ffffff;
  border: 1px solid #e9e9e9;
  border-top-width: 0px;
  position: relative;
  transition: margin-top 500ms linear 20ms, opacity 200ms, z-index 500ms;
  z-index: -1;
  opacity: 0;
}
.content.open {
  opacity: 1;
  transition: margin-top 500ms, opacity 300ms linear 300ms;
  z-index: 1;
}
</style>

