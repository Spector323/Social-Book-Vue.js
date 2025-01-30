<template>
  <main>
    <div class="container">
      <input type="text" placeholder="Новый пост ..." v-model="text">
      <button @click="addPost()">Добавить</button>
    </div>

    <Posts :posts="posts" @updatePost="updatePost" @deletePost="deletePost" />
  </main>
</template>

<script>
import Posts from './components/Posts.vue';

export default {
  components: { Posts },
  data() {
    return {
      posts: [
        {
          id: 1,
          text: "Сегодня было замечательное предложение пойти поужинать этим вечером. Главное, чтобы погода была преимущественно теплой.",
          comments: []
        }
      ],
      text: ""
    };
  },
  methods: {
    addPost() {
      if (this.text.trim() === "") return;
      const newPost = {
        id: this.posts.length + 1,
        text: this.text,
        comments: []
      };
      this.posts.push(newPost);
      this.text = "";
    },
    updatePost(updatedPost) {
      const index = this.posts.findIndex(post => post.id === updatedPost.id);
      if (index !== -1) {
        this.posts[index].text = updatedPost.text;
      }
    },
    deletePost(postId) {
      this.posts = this.posts.filter(post => post.id !== postId);
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  gap: 20px;
  background-color: white;
  padding: 20px;
  border-radius: 15px;
  border: 2px solid #0094FF;
}
input {
  border: 1px solid #777;
  border-radius: 15px;
  padding: 10px;
  font-size: 20px;
  width: 561px;
}
button {
  width: 177px;
  height: 51px;
  background-color: #216CFF;
  color: white;
  border-radius: 15px;
  border: none;
  font-size: 20px;
  cursor: pointer;
  transition: all 0.2s;
}
button:hover {
  opacity: 0.8;
}
</style>
