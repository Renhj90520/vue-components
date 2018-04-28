<template>
<div id="host">
  <div id="line">
      <span class="timeline-dot"></span>
  </div>
  <app-timeline-item></app-timeline-item>
  <app-timeline-item></app-timeline-item>
  <div class="oper-wrapper" @mouseenter="showTip=true" @mouseleave="showTip=false">
      <a href="#" id="last-oper">
        <app-tooltip message="load more" :show="showTip"></app-tooltip>
        <i class="fa fa-plus"></i>
      </a>
  </div>
</div>
</template>
<script>
import TimelineItem from './TimelineItem';
import Tooltip from './Tooltip';
export default {
  data() {
    return {
      showTip: false
    };
  },
  components: {
    'app-timeline-item': TimelineItem,
    'app-tooltip': Tooltip
  }
};
</script>
<style scoped>
#host {
  position: relative;
  height: 100%;
  width: 100%;
  padding-bottom: 54px;
}
#line {
  width: 2px;
  height: 100%;
  background-color: #e1e1e1;
  position: absolute;
  left: 86px;
  margin-bottom: 50px;
}
.timeline-dot {
  width: 6px;
  height: 6px;
  background-color: #e8e8e8;
  border-radius: 50%;
  position: absolute;
  top: -6px;
  left: -2px;
}
.oper-wrapper {
  position: absolute;
  left: 58px;
}
#last-oper {
  width: 54px;
  height: 54px;
  border: 3px solid #e8e8e8;
  border-radius: 50%;
  display: block;
  position: relative;
  background-color: white;
  text-align: center;
  font-size: 20px;
  line-height: 48px;
}
#last-oper i {
  background-color: #37bdb5;
  color: white;
  border-radius: 50%;
  width: 26px;
  height: 26px;
  line-height: 26px;
}
</style>

