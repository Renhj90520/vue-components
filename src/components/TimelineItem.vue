<template>
    <div id="itemhost">
        <div class="icon">
            <i class="fa fa-camera"></i>
            <span class="circle"></span>
        </div>
        <div class="entry-body">
            <header>
                <span class="triangle"></span>
                <h4 class="title">
                <a href="#">This is sample standard blog post</a>
                </h4>
                <span>
                <i class="fa fa-user"></i>
                <a href="#">Admin</a>
                </span>
                <span>
                <i class="fa fa-clock-o"></i>
                <a href="#">17-08-2013</a>
                </span>
                <span>
                <i class="fa fa-comments"></i>
                <a href="#">12 comments</a>
                </span>
                <span>
                <i class="fa fa-suitcase"></i>
                <a href="#">Tutorials</a>
                </span>
            </header>
            <div class="entry-content clearfix">
                <div class="entry-thumb hover-effect" @mouseenter="isMaskShow=true" @mouseleave="isMaskShow=false">
                <transition name="slide">
                    <div class="mask" v-show="isMaskShow">
                        <a href="#">
                        <i class="fa fa-plus"></i>
                        </a>
                    </div>
                </transition>
                <img src="http://www.placehold.it/200x200" alt="">
                </div>
                <p>This is the default format for a blog post. This post type has a large and single image at the beginning. All blog styles
                are equipped with the tag mechanism, social sharing widget, author introduction, related posts, and comment box with
                reply.
                </p>
                <a class="more-link ajax" href="news-standard.html">Read more</a>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      isMaskShow: false
    };
  }
};
</script>
<style scoped>
#itemhost {
  position: relative;
  width: 100%;
  display: flex;
  margin: 0px 0 20px;
}
.icon {
  position: relative;
  margin-top: 25px;
  flex: 0 0 125px;
}
.icon i {
  margin: 0;
  width: 60px;
  height: 60px;
  border: 3px solid #e8e8e8;
  border-radius: 50%;
  font-size: 30px;
  color: #37bdb5;
  text-align: center;
  line-height: 54px;
  background-color: white;
}
.circle {
  width: 18px;
  height: 18px;
  background-color: #37bdb5;
  position: absolute;
  top: 22px;
  left: 77px;
  border-radius: 50%;
  border: 4px solid white;
  display: block;
}

.entry-body {
  background-color: white;
  border: 1px solid white;
  border-radius: 5px;
  flex: 1 1 auto;
}

.entry-body header {
  position: relative;
  border-bottom: 1px solid #ebebeb;
  padding: 15px 20px;
  background-color: #f9f9f9;
  border-radius: 5px 5px 0 0;
}
header a {
  color: #3d3d3d;
  text-decoration: none;
}
header a:hover {
  color: #37bdb5;
}
.title {
  font-size: 18px;
}

header span a,
header span i {
  color: #898989;
  font-size: 11px;
  display: inline-block;
}
header span a:hover {
  color: #37bdb5;
}
header span {
  margin-right: 25px;
}
.entry-content {
  padding: 20px;
}
.entry-thumb {
  float: left;
  margin-right: 20px;
  position: relative;
}
.mask {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  overflow: hidden;
  transition: opacity 200ms ease-in, left 300ms ease-in;
  left: 0;
}
.mask a {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-left: -20px;
  margin-top: -20px;
  width: 40px;
  height: 40px;
  border: 2px solid white;
  border-radius: 50%;
  text-align: center;
  color: white;
  line-height: 36px;
  font-size: 20px;
}
.triangle {
  width: 10px;
  height: 20px;
  display: block;
  position: absolute;
  background-image: url('../assets/images/triangle-timeline.png');
  background-repeat: no-repeat;
  top: 50%;
  left: -10px;
}
.slide-enter {
  opacity: 0;
  left: 100%;
}
.slide-enter-active {
}
.slide-leave {
}
.slide-leave-active {
  opacity: 0;
  left: 100%;
}
</style>
