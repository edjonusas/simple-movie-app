<template>
  <div class="home">
    <h1>Best Movies List</h1>
    <button @click="addMovieMenu">Add Your Movie</button>
    <div v-if="AddMenuVisible">
      <add-movie-menu @close-menu="addMovieMenu" />
    </div>
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
import AddMovieMenu from '@/components/AddMovieMenu'
import MovieCard from '@/components/MovieCard'
export default {
  name: 'Home',
  components: {
    MovieCard,
    AddMovieMenu,
  },
  data() {
    return {
      AddMenuVisible: false,
    }
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
    addMovieMenu() {
      this.AddMenuVisible = !this.AddMenuVisible
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
button {
  padding: 10px;
  margin-bottom: 40px;
}
</style>
