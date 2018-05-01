<template>
  <div class="tabpanle-host">
    <ul>
        <li v-for=" (item,index) in items" :class="{'active':index===current}" :key="item.title">
            <a @click="active(index)">{{item.title}}</a>
        </li>
    </ul>
    <div class="content">
        {{content}}
    </div>
  </div>
</template>
<script>
export default {
  props: ['items'],
  data() {
    return {
      current: 0,
      content: ''
    };
  },
  methods: {
    active(index) {
      this.current = index;
      this.content = this.items[this.current].content;
    }
  },
  created() {
    this.active(0);
  }
};
</script>
<style scoped>
.tabpanel-host {
  position: relative;
}
ul {
  list-style: none;
  padding: 0;
  margin: 18px 0 13px;
}
li {
  display: inline-block;
  cursor: pointer;
}
a {
  text-decoration: none;
  color: #555;
  font-size: 14px;
  padding: 15px 23px;
  border: 1px solid #e9e9e9;
  background-color: #fafafa;
  box-shadow: inset 0 0 3px #f5f5f5;
}
li.active a {
  border-top: 2px solid #07cdec;
  border-bottom: 1px solid white;
  background-color: white;
  box-shadow: none;
}
.content {
  border: 1px solid #e9e9e9;
  top: 33px;
  left: 0;
  padding: 20px;
  background-color: #fff;
}
</style>

