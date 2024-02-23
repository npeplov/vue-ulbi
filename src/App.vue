<template>
  <div>
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <input
        v-bind:value="title"
        type="text"
        class="input"
        placeholder="Название"
        @input="title = $event.target.value"
      />
      <input
        v-bind:value="body"
        type="text"
        class="input"
        placeholder="Описание"
        @input="body = $event.target.value"
      />
      <button @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div><strong>Название: </strong>{{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
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
      title: "",
      body: "",
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      };
      this.posts.push(newPost);
      (this.title = ""), (this.body = "");
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

.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
</style>
