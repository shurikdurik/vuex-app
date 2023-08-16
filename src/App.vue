<template>
    <PostForm />
    <h1>{{ postsCount }}</h1>
    <div class="post" v-for="post of validPosts">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import PostForm from './components/PostForm.vue'
export default {
  name: 'App',
  components: {
    PostForm
  },
  /* computed: {
    allPosts() {
      this.$store.getters.allPosts
    }
  } */
  methods: mapActions(["fetchPosts"]),
  computed:  mapGetters([ "validPosts", "postsCount" ]),
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
  padding: 0 50px;

}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}
</style>
