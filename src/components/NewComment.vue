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
input {
  background: none;
  border-radius: 4px;
  border: 2px solid #157970;
  outline: none;
  color: #0c3f3b;
  font-size: 18px;
  padding: 12px 10px;
  margin-bottom: 10px;
}

input::placeholder,
textarea::placeholder {
  color: #157971b7;
}

textarea {
  outline: none;
  resize: none;
  border-radius: 4px;
  border: 2px solid #157970;
  background: none;
  font-size: 18px;
  padding: 12px 10px;
  height: 100px;
}

button {
  outline: none;
  font-size: 18px;
  font-weight: 600;
  border-radius: 4px;
  color: #157970;
  border-radius: 4px;
  border: 2px solid #157970;
  width: 180px;
  margin: 10px 10px;
  padding: 12px 10px;
}

.error {
  border: 2px red solid;
  transition: 1s;
}
</style>
