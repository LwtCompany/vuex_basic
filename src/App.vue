<template>
  <div id="app">
    <PostForm></PostForm>
    <h1>{{postsCount}}</h1>
    <div class="posts" v-for="(post, index) in validPosts" :key="post.id" v-on:click="test(post.id)">
      
        <h2>{{index +") "+ post.title}}</h2>
        <p>{{post.body}}</p>
        <span>{{post.id}}</span>
    </div>
  </div>
</template>

<script>
  
  import {mapGetters, mapActions} from "vuex";
  import PostForm from "./components/PostForm";

    export default {
      name: "App",
      components: {PostForm},
      computed: mapGetters(["validPosts", "postsCount"]),
      methods: mapActions(["fetchPosts", "test"]),

      async mounted() {
        this.fetchPosts(4);
      },
      
  
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
  width: 400px;
  margin-top: 50px;
  margin: 0px auto;
}

.posts{
  border: 1px solid grey;
  margin: 0 auto;
  margin-top: 5px;
  width: auto;
}
</style>
