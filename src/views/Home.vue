<template>
  <div class="home">
    <h1>Best Movies List</h1>
    <div class="movies-block">
      <movie-card
        v-for="movie in movies"
        @click="goMovie(movie.id)"
        :key="movie.id"
        :movie="movie"
      />
    </div>
  </div>
</template>

<script>
import MovieCard from '@/components/MovieCard'
export default {
  name: 'Home',
  components: {
    MovieCard,
  },
  computed: {
    movies() {
      return this.$store.getters.getMovies
    },
  },
  methods: {
    goMovie(id) {
      this.$store.commit('setMovieSingle', id)
      this.$router.push(`/movie/${id}`)
    },
  },
}
</script>

<style scoped>
.movies-block {
  margin: 0 auto;
  max-width: 890px;
  gap: 30px;
  display: flex;
  flex-wrap: wrap;
}
</style>
