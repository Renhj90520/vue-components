<template>
    <div class="roundcontrol-host">
        <a @click="showsubs=!showsubs">
            <i class="fa fa-user icon"></i>
            <span>User Actions</span>
        </a>
        <ul :style="{'z-index':showsubs?1:-1}">
            <li
                :class="{controlshow:showsubs}"
                :style="{top:showsubs?sub.top:'50%',left:showsubs?sub.left:'50%','transition-delay':index*100+'ms'}" 
                v-for="(sub,index) in subbtns"
                @mouseenter="showTip(index)" 
                @mouseleave="hideTip(index)" 
                :key="sub.icon">
                <a href="#">
                    <i class="fa" :class="sub.icon"></i>
                    <app-tooltip :message="sub.tip" :show="sub.showTip"></app-tooltip>
                </a>
            </li>
        </ul>
    </div>
</template>
<script>
import Tooltip from './Tooltip';
export default {
  data() {
    return {
      subbtns: [
        {
          icon: 'fa-th-list',
          left: '-52px',
          top: '-52px',
          tip: 'Show list',
          showTip: false
        },
        {
          icon: 'fa-plus',
          left: '2px',
          top: '-72px',
          tip: 'Add new',
          showTip: false
        },
        {
          icon: 'fa-check',
          left: '52px',
          top: '-52px',
          tip: 'Registrations',
          showTip: false
        },
        {
          icon: 'fa-envelope',
          left: '72px',
          top: '2px',
          tip: 'Show mail',
          showTip: false
        },
        {
          icon: 'fa-signal',
          left: '52px',
          top: '52px',
          tip: 'User activity',
          showTip: false
        },
        {
          icon: 'fa-star',
          left: '2px',
          top: '72px',
          tip: 'Top users',
          showTip: false
        },
        {
          icon: 'fa-comment',
          left: '-52px',
          top: '52px',
          tip: 'Last comments',
          showTip: false
        }
      ],
      showsubs: false
    };
  },
  methods: {
    showTip: function(i) {
      this.subbtns[i].showTip = true;
    },
    hideTip: function(i) {
      this.subbtns[i].showTip = false;
    }
  },
  components: {
    'app-tooltip': Tooltip
  }
};
</script>
<style scoped>
.roundcontrol-host {
  width: 108px;
  height: 108px;
  margin: 25px auto;
  position: relative;
  background: linear-gradient(to top, #ffffff 0%, #fafafa 100%);
  border-radius: 50%;
  box-shadow: 0 3px 4px rgba(0, 0, 0, 0.2),
    inset 0 1px 3px rgba(255, 255, 255, 0.5);
}
a {
  color: #333;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
}
.roundcontrol-host > a {
  display: inline-block;
  width: 86px;
  height: 86px;
  margin: 11px;
  border: 1px solid #ddd;
  background: #eef1f3;
  background: -moz-linear-gradient(to top, #fff 0%, #dedede 100%);
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    color-stop(0%, #ffffff),
    color-stop(100%, #dedede)
  );
  background: -webkit-linear-gradient(to top, #fff 0%, #dedede 100%);
  background: -o-linear-gradient(to top, #ffffff 0%, #dedede 100%);
  background: -ms-linear-gradient(to top, #ffffff 0%, #dedede 100%);
  background: linear-gradient(to top, #ffffff 0%, #dedede 100%);
  box-shadow: 0 1px 0 rgba(255, 255, 255, 0.6),
    inset 0 1px 2px rgba(0, 0, 0, 0.3);
  border-radius: 50%;
}
.icon {
  margin: 10px 0 0;
  font-size: 30px;
  display: block;
}
.roundcontrol-host > a > span {
  font-size: 11px;
  font-weight: bold;
  line-height: 13px;
  width: 74px;
  display: block;
  text-align: center;
  margin: 10px auto 0;
}
ul {
  list-style: none;
  padding: 0;
  position: absolute;
  z-index: 1;
  top: 40px;
  left: 40px;
  z-index: -1;
}
li {
  position: absolute;
  box-shadow: 0 0 2px #d9d9d9;
  transition: all 100ms ease-in-out;
}
li a {
  position: relative;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 1px solid #ccc;
  background-color: #fcfcfc;
  text-align: center;
  line-height: 30px;
  font-size: 14px;
  display: block;
}
</style>

