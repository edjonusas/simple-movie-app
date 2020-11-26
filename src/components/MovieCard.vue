<template>
  <div class="movie-card">
    <img :src="movie.image" :alt="movie.title" />
    <h2 class="title">{{ movie.title }}</h2>
    <div class="info-block">
      <span class="year">Year: {{ movie.year }}</span>
      <span class="rating">Rating: {{ movie.rating }} </span>
    </div>
    <span class="comments"> {{ movie.comments.length }} comments</span>
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  props: {
    movie: Object,
  },
}
</script>

<style scoped>
.movie-card {
  width: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

img {
  object-fit: cover;
  width: 182px;
  height: 268px;
}
.info-block {
  display: flex;
  gap: 10px;
  justify-content: space-between;
}

span {
  display: inline-block;
  margin: 5px 0;
}

.title {
  font-size: 20px;
  margin: 10px 0;
}
</style>
