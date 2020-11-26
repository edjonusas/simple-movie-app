<template>
  <button @click="back">Back to movie list</button>
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
  methods: {
    back() {
      this.$router.push('/')
    },
  },
}
</script>

<style scoped>
button {
  background: none;
  outline: none;
  font-size: 18px;
  font-weight: 600;
  border-radius: 4px;
  color: #157970;
  border-radius: 4px;
  border: 2px solid #157970;
  width: 180px;
  margin: 50px 10px 10px;
  padding: 12px 10px;
}
</style>
