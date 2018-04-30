<template>
  <div class="collapsepanel-host" ref="el">
    <a class="toggle" :class="{'collapse':!state}" @click="toggle()">
        <i class="fa" :class="{'fa-plus':!state,'fa-minus':state}"></i>
    </a>
    <div class="info-wrapper">
        <div class="title">
            <a class="toggle-title" @click="toggle()">
            {{title}}
            </a>
        </div>
        <div class="content" ref="content">
            <slot></slot>
        </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['title'],
  data() {
    return {
      state: false
    };
  },
  methods: {
    toggle() {
      this.state = !this.state;
      const contentHeight = this.$refs.content.clientHeight;
      if (this.state) {
        this.$refs.el.style.height = contentHeight + 40 + 'px';
      } else {
        this.$refs.el.style.height = '40px';
      }
    }
  }
};
</script>
<style scoped>
.collapsepanel-host {
  display: flex;
  height: 40px;
  overflow: hidden;
  background-color: transparent;
  transition: all 500ms;
}
a {
  text-decoration: none;
  cursor: pointer;
}
.toggle {
  display: inline-block;
  color: white;
  height: 40px;
  line-height: 40px;
  padding: 0 8px;
  background-color: #4e5257;
}
.toggle.collapse {
  background-color: #b6d82f;
}
.info-wrapper {
  border: 1px solid #dfdfdf;
  background-color: #f7f7f7;
  width: 100%;
}
.title {
  display: inline-block;
  height: 40px;
  line-height: 40px;
  padding: 0 10px;
}
.title a {
  color: #4e5257;
  font-size: 1.2em;
}
.content {
  padding: 0 10px 10px 15px;
  color: #8d8d8d;
  height: auto;
}
</style>

