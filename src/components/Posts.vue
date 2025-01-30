<template>
  <div class="post-container">
    <div class="pt-cn" v-for="post in posts" :key="post.id">
      <p>{{ post.text }}</p>
      <hr>
      <div class="cn-block">
        <button class="bn-cl" @click="toggleComments(post)">Комментарии</button>
        <span>Количество комментариев - {{ post.comments.length }}</span>
        <button class="bn-cl" @click="editPost(post)">Изменить</button>
        <button class="bn-vl" @click="$emit('deletePost', post.id)">Удалить</button>
      </div>

      <div v-if="post.showComments" class="cn-bl">
        <div class="cn-kl">
          <input v-model="post.newComment" placeholder="Новый комментарий ..." />
          <button @click="addComment(post)" class="bn-cl">Добавить</button>
        </div>
        <div v-for="(comment, index) in post.comments" :key="index" class="comment">
          <input v-model="post.comments[index]" />
          <button @click="deleteComment(post, index)" class="bn-vl">Удалить</button>
        </div>
        <button @click="toggleComments(post)" class="bn-cl" style="width: 120px;">Спрятать</button>
      </div>
    </div>

    <EditPost v-if="showEditPost" :post="currentPost" @close="showEditPost = false" @confirm="updatePost" />
  </div>
</template>

<script>
import EditPost from "./EditPost.vue";

export default {
  components: { EditPost },
  props: {
    posts: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      showEditPost: false,
      currentPost: null
    };
  },
  methods: {
    toggleComments(post) {
      post.showComments = !post.showComments;
    },
    addComment(post) {
      if (post.newComment.trim() !== "") {
        post.comments.push(post.newComment);
        post.newComment = "";
      }
    },
    deleteComment(post, index) {
      post.comments.splice(index, 1);
    },
    editPost(post) {
      this.currentPost = { ...post };
      this.showEditPost = true;
    },
    updatePost(updatedPost) {
      this.$emit("updatePost", updatedPost);
      this.showEditPost = false;
    }
  }
};
</script>

<style >
.post-container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
  margin-top: 60px;
}

.pt-cn {
  background-color: white;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  border: 2px solid #0094FF;
  border-radius: 15px;
}

.pt-cn p {
  font-size: 20px;
}

.cn-block {
  display: grid;
  grid-template-columns: 160px 1fr 120px 120px;
  gap: 10px;
  text-align: center;
  align-items: center;
}

button {
  color: white;
  border-radius: 15px;
  border: none;
  font-size: 18px;
  cursor: pointer;
  transition: all 0.2s;
  padding-block: 10px;
}

button:hover {
  opacity: 0.9;
}

.cn-bl {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 10px;
}

.cn-kl {
  display: flex;
  gap: 10px;
  align-items: center;
}

input {
  border: 1px solid #777;
  border-radius: 15px;
  padding: 10px;
  font-size: 20px;
  width: 100%;
}

.bn-cl {
  background-color: #216CFF;
  padding: 10px;
}

.bn-vl {
  background-color: #FF218B;
  padding: 10px;

}

.comment {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-top: 5px;
}

hr {
  border: 0;
  height: 1px;
  background: #ddd;
  margin: 10px 0;
}
</style>