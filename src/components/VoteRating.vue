<template>
    <div class="vote-host" ref="host">
        <a @click="dovote(0)" @mouseenter="dohover(0)">
            <i class="fa fa-star" :class="{'active':states[0]}"></i>
        </a>
        <a @click="dovote(1)" @mouseenter="dohover(1)">
            <i class="fa fa-star" :class="{'active':states[1]}"></i>
        </a>
        <a @click="dovote(2)" @mouseenter="dohover(2)">
            <i class="fa fa-star" :class="{'active':states[2]}"></i>
        </a>
        <a @click="dovote(3)" @mouseenter="dohover(3)">
            <i class="fa fa-star" :class="{'active':states[3]}"></i>
        </a>
        <a @click="dovote(4)" @mouseenter="dohover(4)">
            <i class="fa fa-star" :class="{'active':states[4]}"></i>
        </a>
    </div>
</template>
<script>
export default {
  data() {
    return {
      states: [false, false, false, false, false],
      current: 0
    };
  },
  props: ['currentValue'],
  methods: {
    setActive(index) {
      for (let i = 0; i <= index; i++) {
        this.states.splice(i, 1, true);
      }
      const left = +index + 1;
      for (let j = left; j < this.states.length; j++) {
        this.states.splice(j, 1, false);
      }
    },
    reset() {
      this.current = this.currentValue;
      this.setActive(this.current);
    },
    dohover(index) {
      this.setActive(index);
    },
    dovote(index) {
      this.current = index;
      this.setActive(this.current);
      this.$emit('vote', this.current);
    }
  },
  mounted() {
    this.current = this.currentValue;
    this.setActive(this.currentValue);
    this.$refs.host.onmouseleave = () => {
      this.setActive(this.current);
    };
  }
};
</script>
<style scoped>
a {
  display: inline-block;
  cursor: pointer;
  font-size: 15px;
  color: #333;
}
.active {
  color: #ffd118;
}
</style>
