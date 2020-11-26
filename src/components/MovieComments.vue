<template>
  <div class="comments-block">
    <div class="info-block">
      <h3>{{ comment.name }}</h3>
      <p>{{ comment.comment }}</p>
    </div>
    <div class="button-block">
      <button @click="deleteComment">&#10006;</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MovieComments',
  props: {
    comment: Object,
  },
  methods: {
    deleteComment() {
      this.$emit('delete-comment')
    },
  },
}
</script>

<style scoped>
.comments-block {
  border: 2px solid #157970;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}
.info-block {
  box-sizing: border-box;
  padding: 20px 40px;
  width: 900px;
  text-align: left;
}
.button-block {
  width: 100px;
}

button {
  color: #0c3f3b;
  border: none;
  background: none;
  font-weight: 700;
  font-size: 25px;
}
</style>
