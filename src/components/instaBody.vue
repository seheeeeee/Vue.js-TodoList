<template>
  <div class="instaBody">
      <div v-if="step === 1" class="feed">
          <insta-post v-for="post in posts" v-bind:post="post" v-bind:key="posts.indexOf(post)"></insta-post>
      </div>
      <div v-if="step === 2">
          <div class="selectedImage" :class="selectedFilter" :style="{ backgroundImage: 'url('+image+')'}">
          </div>
          <div class="filterContainer">
              <filter-type v-for="filter in filters"
                v-bind:filter="filter"
                v-bind:image="image"
                v-bind:key="filters.indexOf(filter)">
              </filter-type>
          </div>
      </div>
  </div>
</template>

<script>
import instaPost from './instaPost.vue'
import filterType from './filterType.vue'

export default {
    name: "instaBody",
    props: {
        step: Number,
        posts: Array,
        filters: Array,
        image: String,
        selectedFilter: String,
    },
    components: {
        'insta-post': instaPost,
        'filter-type': filterType,
    }
}
</script>

<style>
    .instaBody{
        height: 100%;
    }
    .feed{
        height: 100%;
        overflow-x: hidden;
        overflow-y: scroll;
        margin-right: -15px;
    }
    .selectedImage{
        padding-top: 50px;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        height: 330px;
    }
    .filterContainer{
        height: 220px;
        padding: 30px 10px;
        white-space: nowrap;
        overflow-x: scroll;
    }
</style>