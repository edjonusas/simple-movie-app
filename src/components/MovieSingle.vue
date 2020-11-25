<template>
  <div class="movie-block">
    <div class="movie-left">
      <div>
        <img :src="movie.image" :alt="movie.title" />
      </div>
      <div class="movie-info">
        <h1>{{ movie.title }}</h1>
        <span class="year">Year: {{ movie.year }}</span>
        <span class="rating">Rating: {{ movie.rating }} </span>
        <p class="description">{{ movie.description }}</p>
      </div>
    </div>
    <div class="comments">
      <movie-comments
        v-for="(comment, index) in movie.comments"
        :key="index"
        @delete-comment="deleteComment(index)"
        :comment="comment"
      />
    </div>
    <div><new-comment @comment="sendComment" /></div>
  </div>
</template>

<script>
import MovieComments from '@/components/MovieComments'
import NewComment from './NewComment'
export default {
  name: 'MovieSingle',
  components: {
    MovieComments,
    NewComment,
  },
  props: {
    movie: Object,
  },
  methods: {
    sendComment(comment) {
      this.$store.commit('sendComment', comment)
    },
    deleteComment(id) {
      this.$store.commit('deleteComment', { commentId: id, movieId: this.$route.params.id })
    },
  },
}
</script>

<style scoped>
.movie-block {
  margin: 0 auto;
  width: 1000px;
}
.movie-left {
  display: flex;
  align-items: center;
  margin: 30px 0 60px;
}
.movie-left div {
  width: 50%;
}

.movie-info span {
  margin: 0 10px;
}
</style>
