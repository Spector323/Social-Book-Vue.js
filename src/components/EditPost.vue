<template>
    <div class="modal">
      <div class="modal-content">
        <textarea v-model="editedText"></textarea>
        <div class="buttons">
          <button class="bn-cl" @click="confirmEdit">Подтвердить</button>
          <button class="bn-vl" @click="$emit('close')">Закрыть</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      post: Object
    },
    data() {
      return {
        editedText: this.post.text
      };
    },
    methods: {
      confirmEdit() {
        this.$emit("confirm", { ...this.post, text: this.editedText });
      }
    }
  };
  </script>
  
  <style scoped>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #6c9dff98;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal-content {
    background: white;
    padding: 30px 20px;
    border-radius: 15px;
    text-align: center;
  }
  textarea {
    width: 751px;
    height: 113px;
    border-radius: 15px 0px 0px 0px;
    border: 1px solid #666;
    font-size: 24px;
    padding: 9px 18px;
    border-radius: 15px;
  }
  .buttons {
    display: flex;
    justify-content: end;
    gap: 28px;
    margin-top: 20px;
  }
  button {
    padding: 10px 15px;
    font-size: 16px;
    border: none;
    cursor: pointer;
    border-radius: 15px;
  }
  .close-btn {
    background: #FF218B;
    color: white;
  }
  </style>
  