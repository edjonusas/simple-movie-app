<template>
  <!-- <router-link to="/">Movie list</router-link> -->
  <router-view />
</template>

<script>
// Movie gallery application
//done you are given movie list
//done first page of application should be movie gallery with movie cards
//done each cart should have: title, year, rating, comments length, and cover image
//done clicking on the card should redirect you to other page with information about particular movie
//done in movie information page this info is displayed: title, year, rating, description, image and comments
//done also in movie details page you should be able to add new comment and delete any comment
//done (remember to validate comment inputs, so user could not add empty text as comment)
// also create modal to add new movie if needed
// make sure to use these methods at least once:
// class binding, style binding, v-for, v-if, at least one lifecycle hook
// CREATIVE TASK:
// think of some new cool feature in your application, so you could use "watch" method in it
</script>

<style>
body {
  background-image: url('../src/assets/img/bg.jpg');
  background-position: center;
  background-size: cover;
}
#app {
  /* filter: grayscale(90%); */
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}
</style>
