<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <MyButton @click="showDialog" style="margin-top: 15px;">Создать пост</MyButton>
    <MyDialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </MyDialog>
    <PostList @remove="removePost" :posts="posts" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
export default {
  components: {
    PostForm,
    PostList,
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
      dialogVisible: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 15px;
}
</style>
