<template>
  <div class="home">
    <div class="top-header">
      <h1>Best Movies List</h1>
      <button @click="addMovieMenu">Add Your Movie</button>
    </div>
    <div v-if="AddMenuVisible">
      <add-movie-menu @add-movie="addMovie" @close-menu="addMovieMenu" />
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
    addMovie(movie) {
      this.$store.commit('addMovie', movie)
    },
  },
}
</script>

<style scoped>
.top-header {
  background-color: #e6e6e695;
  padding: 10px 0 30px;
  margin-bottom: 20px;
}
h1 {
  color: #0c3f3b;
  margin: 0;
  margin-bottom: 20px;
}
.movies-block {
  margin: 0 auto;
  max-width: 890px;
  gap: 30px;
  display: flex;
  flex-wrap: wrap;
}
button {
  font-size: 18px;
  font-weight: 600;
  border-radius: 4px;
  color: #157970;
  border: #157970 2px solid;
  background: none;
  padding: 10px;
  outline: none;
}
</style>
