<template>
  <div class="movie">
    <movie-single :movie="movie" />
  </div>
</template>

<script>
import MovieSingle from '../components/MovieSingle'
export default {
  name: 'Movie',
  components: {
    MovieSingle,
  },
  computed: {
    movie() {
      if (this.$store.getters.getSingleMovie !== null) {
        return this.$store.getters.getSingleMovie
      } else {
        this.$store.commit('setMovieSingle', this.$route.params.id)
        return this.$store.getters.getSingleMovie
      }
    },
  },
}
</script>
