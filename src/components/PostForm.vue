<template>
  <form @submit.prevent>
    <h4>Создать поста</h4>
    <my-input
        v-model="post.title"
        type="text"
        placeholder="Название" />
    <my-input
        v-model="post.body"
        type="text"
        placeholder="Описание" />
    <my-button
        class="btn"
        style="align-self: flex-end; margin-top: 15px"
        @click="createPost"
        >
      Создать
    </my-button>
  </form>
</template>

<script>
import MyInput from "@/components/UI/MyInput.vue";
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components: {MyButton, MyInput},
    data() {
      return {
        post: {
          title: '',
          body: '',
        }
      }
    },
  methods: {
      createPost(){
        this.post.id = Date.now();
        this.$emit('create', this.post)
        this.post = {
         title: '',
         body: '',
       }
      }
  }
}
</script>

<style lang="css" scoped>
form {
  display: flex;
  flex-direction: column;
}

</style>
