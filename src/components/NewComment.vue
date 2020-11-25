<template>
  <div v-if="errorMessage">{{ errorMessage }}</div>
  <form @submit.prevent="sendComment" class="comment-form">
    <div class="inputs">
      <input v-model="name" type="text" placeholder="Name" />
      <textarea v-model="comment" placeholder="Your Comment..."></textarea>
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
      name: '',
      comment: '',
      errorMessage: '',
    }
  },
  methods: {
    sendComment() {
      if (this.name.length === 0) {
        return (this.errorMessage = 'Enter your name')
      }
      if (this.comment.length < 10) {
        return (this.errorMessage = 'Comment must be longer then 10 symbols')
      }
      this.$emit('comment', {
        name: this.name,
        comment: this.comment,
        movieId: this.$route.params.id,
      })
      ;(this.name = ''), (this.comment = ''), (this.errorMessage = '')
    },
  },
}
</script>

<style scoped>
.comment-form {
  margin: 10px auto;
  max-width: 600px;
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