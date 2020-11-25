<template>
  <div v-if="errorMessage">{{ errorMessage }}</div>
  <form @submit.prevent="sendComment" class="comment-form">
    <div class="inputs">
      <input :class="{ error: nameError }" v-model="name" type="text" placeholder="Name" />
      <textarea
        :class="{ error: commentError }"
        v-model="comment"
        placeholder="Your Comment..."
      ></textarea>
    </div>
    <div>
      <button>Send Comment</button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'NewComment',
  watch: {
    nameError: function () {
      setTimeout(() => {
        this.nameError = false
      }, 3000)
    },
    commentError: function () {
      setTimeout(() => {
        this.commentError = false
      }, 3000)
    },
  },
  data() {
    return {
      name: '',
      comment: '',
      errorMessage: '',
      nameError: false,
      commentError: false,
    }
  },
  methods: {
    sendComment() {
      if (this.name.length === 0) {
        return (this.errorMessage = 'Enter your name'), (this.nameError = true)
      }
      if (this.comment.length < 10) {
        return (
          (this.errorMessage = 'Comment must be longer then 10 symbols'), (this.commentError = true)
        )
      }
      this.$emit('comment', {
        name: this.name,
        comment: this.comment,
        movieId: this.$route.params.id,
      })
      ;(this.name = ''), (this.comment = ''), (this.errorMessage = '')
    },
  },
  emits: ['comment'],
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

.error {
  border: 2px red solid;
  transition: 1s;
}
</style>
