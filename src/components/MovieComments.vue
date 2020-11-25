<template>
  <div class="comments-block">
    <div class="info-block">
      <h3>{{ comment.name }}</h3>
      <p>{{ comment.comment }}</p>
    </div>
    <div class="button-block">
      <button @click="deleteComment">Delete</button>
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
  display: flex;
  align-items: center;
}
.info-block {
  box-sizing: border-box;
  padding: 20px 40px;
  margin: 10px 0;
  background: #f8f8f8;
  width: 900px;
  text-align: left;
}
.button-block {
  width: 100px;
}
</style>