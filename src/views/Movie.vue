<template>
  <div class="movie">
    <movie-single />
  </div>
</template>

<script>
import MovieSingle from '../components/MovieSingle'
export default {
  name: 'Movie',
  components: {
    MovieSingle,
  },
}
</script>
