<template>
  <div class="app">
    <PostForm @create="createPost"/>
    <PostList :posts="posts"
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm"
import PostList from "@/components/PostList"
export default {
  components: {
    PostForm,
    PostList
  },
  data() {
    return {
      posts: [
        {
          id: 1,
          title: "Javascript",
          body: "Lorem, ipsum dolor sit amet consectetur!",
        },
        {
          id: 2,
          title: "Javascript 2",
          body: "Lorem, ipsum dolor sit amet consectetur!2",
        },
        {
          id: 3,
          title: "Javascript 3",
          body: "Lorem, ipsum dolor sit amet consectetur!3",
        },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
    }
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}


</style>
