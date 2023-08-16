<template>
    <h1>{{ postsCount }}</h1>
    <div class="post" v-for="post of allPosts">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'App',
  /* computed: {
    allPosts() {
      this.$store.getters.allPosts
    }
  } */
  methods: mapActions(["fetchPosts"]),
  computed:  mapGetters([ "allPosts", "postsCount" ]),
  mounted() {
    //this.$store.dispatch('fetchPosts')
    this.fetchPosts(5)
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}
</style>
