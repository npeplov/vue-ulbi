<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input
      v-model="post.title"
      type="text"
      class="input"
      placeholder="Название"
    />
    <input
      v-model="post.body"
      type="text"
      class="input"
      placeholder="Описание"
    />
    <MyButton 
    style="align-self: flex-end; margin-top: 15px;" 
    @click="createPost"
      >Создать</MyButton
    >
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton";
export default {
  components: {
    MyButton,
  },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped></style>
