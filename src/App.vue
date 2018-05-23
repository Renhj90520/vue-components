<template>
<div id="app">
  <div class="space">
    <app-down-arrow></app-down-arrow>
    <app-slide-menu></app-slide-menu>
  </div>
  <div class="container">
    <app-timeline></app-timeline>
  </div>
  <app-hi-icon icon="fa-amazon"></app-hi-icon>
  <app-roundcontrol></app-roundcontrol>
  <app-vote-rating :currentValue="3" @vote="dovote($event)"></app-vote-rating>
  <app-galleryitem :img="image"></app-galleryitem>
  <app-collapsepanel title="Title">
    <p>
      Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy
      text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
      It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.
    </p>
    <p>
      It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with
      desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
    </p>
  </app-collapsepanel>
  <app-collapse-another title="Title">
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus varius ligula et enim posuere ac hendrerit eros varius.
      Mauris ut sollicitudin odio. Aliquam in facilisis massa. Donec vel est adipiscing dui congue bibendum. Aliquam aliquam
      sollicitudin euismod. Fusce sit amet scelerisque urna. Curabitur ultrices velit sed metus dignissim venenatis. Vivamus
      urna augue, tincidunt at semper eget, tincidunt vel est. Donec vitae tortor nec orci mattis lobortis. Vivamus id libero
      est. Proin quis nunc non tortor ornare tempor fermentum at dolor. Cras vel turpis magna.</p>
  </app-collapse-another>
  <app-slide-carousel :items="carouselItems"></app-slide-carousel>
  <app-roll-carousel :items="carouselItems" :showItemNum="4"></app-roll-carousel>
  <app-tabpanel-blue :items="tabitems"></app-tabpanel-blue>
  <app-canvas></app-canvas>
</div>
</template>

<script>
import DownArrow from './components/DownArrow';
import SlideMenu from './components/SlideMenu';
import Timeline from './components/Timeline';
import HiIcon from './components/HiIcon';
import RoundControl from './components/RouncControl';
import VoteRating from './components/VoteRating';
import GalleryItem from './components/GalleryItem';
import CollapsePanel from './components/CollapsePanel';
import CollapsePanelAnthor from './components/AnotherCollapsePanel';
import AnotherCollapsePanelVue from './components/AnotherCollapsePanel.vue';
import RollCarousel from './components/RollCarousel';
import SlideCarousel from './components/SlideCarousel';
import TabPanelBlue from './components/TabPanelBlue';
import Canvas from './components/canvas';
export default {
  name: 'App',
  components: {
    'app-down-arrow': DownArrow,
    'app-slide-menu': SlideMenu,
    'app-timeline': Timeline,
    'app-hi-icon': HiIcon,
    'app-roundcontrol': RoundControl,
    'app-vote-rating': VoteRating,
    'app-galleryitem': GalleryItem,
    'app-collapsepanel': CollapsePanel,
    'app-collapse-another': AnotherCollapsePanelVue,
    'app-slide-carousel': SlideCarousel,
    'app-roll-carousel': RollCarousel,
    'app-tabpanel-blue': TabPanelBlue,
    'app-canvas': Canvas
  },
  methods: {
    dovote(e) {
      console.log(e);
    }
  },
  data() {
    return {
      image: {
        src: '/static/images/example_4.jpg',
        title: 'LOREM IPSUM DOLOR',
        description: 'Some description'
      },
      carouselItems: [
        { src: '/static/images/banner-width1.png' },
        { src: '/static/images/banner-width2.png' },
        { src: '/static/images/banner-width3.png' },
        { src: '/static/images/banner-width4.png' },
        { src: '/static/images/banner-width5.png' }
      ],
      tabitems: [
        {
          title: 'Panel One',
          content: `Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua.
    Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
    aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in
    voluptate velitesse cillum dolore eu fugiat nulla pariatur.
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua.`
        },
        {
          title: 'Panel Two',
          content: `Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua 1.
    Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
    aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in
    voluptate velitesse cillum dolore eu fugiat nulla pariatur.
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua.`
        },
        {
          title: 'Panel Three',
          content: `Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua 2.
    Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
    aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in
    voluptate velitesse cillum dolore eu fugiat nulla pariatur.
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua.`
        }
      ]
    };
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
