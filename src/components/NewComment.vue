<template>
  <form @submit.prevent="sendComment" class="comment-form">
    <div class="inputs">
      <input v-model="comment.name" type="text" placeholder="Name" />
      <textarea v-model="comment.comment" required placeholder="Your Comment..."></textarea>
    </div>
    <div>
      <button>Send Comment</button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'NewComment',
  data() {
    return {
      comment: {
        name: '',
        comment: '',
      },
    }
  },
  methods: {
    sendComment() {
      if (this.comment.name === '') {
        this.comment.name = 'Anonymous'
      }
      this.$emit('comment', this.comment)
    },
  },
}
</script>

<style scoped>
.comment-form {
  margin: 10px 0;
  max-width: 900px;
}
.comment-form .inputs {
  display: flex;
  flex-direction: column;
}
input,
textarea {
  padding: 10px 40px;
  margin-bottom: 20px;
}

textarea {
  height: 100px;
}

button {
  padding: 15px 40px;
}
</style>