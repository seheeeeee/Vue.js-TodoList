<template>
  <div id="app">
    <div class="app-phone">
      <insta-header :step="step" v-on:goHomeHeader="goHome"></insta-header>
      <insta-body 
      v-bind:step="step"
      v-bind:posts="posts" 
      v-bind:filters="filters"
      v-bind:image="image"
      v-bind:selectedFilter="selectedFilter">
      <!-- v-model:caption="caption"> -->
      </insta-body>
      <insta-footer v-on:step1="step1" v-on:goHomeFooter="goHome"></insta-footer>
    </div>
  </div>
</template>

<script>
import instaHeader from './components/instaHeader.vue'
import instaBody from './components/instaBody.vue'
import instaFooter from './components/instaFooter.vue'

import posts from './data/post.js'
import filters from './data/filter.js'
import EventBus from './event-bus.js' //부모-자식 사이가 아니여도 자유롭게 사용이 가능함(단, 너무 많이 쓰면 관리 힘듦)

export default {
  data: function(){
    return{
      posts,
      filters,
      step: 1,
      image: "",
      selectedFilter: "",
      caption: "",
    }
  },
  methods: {
    step1: function(image, step){
      this.image = image;
      this.step = step;
    },
    goHome: function(){
      this.image = "";
      this.selectedFilter = "";
      this.caption = "";
      this.step = 1;
    }
  },
  created: function(){
    EventBus.$on("filter-selected", evt => {
      this.selectedFilter = evt.filter;
    });
  },
  components: {
    'insta-header': instaHeader,
    'insta-body': instaBody,
    'insta-footer': instaFooter
  }
}
</script>

<style scoped>
  *{
    margin: 0; padding: 0;
  }
  body{
    background-color: #fff;
  }
  #app{
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .app-phone{
    width: 375px;
    height: 620px;
    overflow: hidden;
    background-color: #fff;
  }
</style>