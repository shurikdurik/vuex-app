<template>
    <div class="post" v-for="post of allPosts">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
</template>

<script>
import { mapGetters } from 'vuex';
export default {
  name: 'App',
  /* computed: {
    allPosts() {
      this.$store.getters.allPosts
    }
  } */
  computed:  mapGetters([ "allPosts" ]),
  mounted() {
    this.$store.dispatch('fetchPosts')
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
