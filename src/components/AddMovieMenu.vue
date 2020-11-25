<template>
  <div class="form">
    <label for="image">Image URL</label>
    <input v-model="image" id="image" type="text" />
    <label for="title">Movie title</label>
    <input v-model="title" id="title" type="text" />
    <label for="year">Movie year</label>
    <input v-model="year" id="year" type="text" />
    <label for="rating">Movie rating</label>
    <input v-model="rating" id="rating" type="text" />
    <label for="description">Movie description</label>
    <textarea v-model="description" id="description"></textarea>
    <div class="button-block">
      <button @click="addMovie">Add Movie</button>
      <button @click="closeMenu">Cancel</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'addMovieMenu',
  data() {
    return {
      image: '',
      title: '',
      year: '',
      rating: '',
      description: '',
      comments: [],
      id: 7,
    }
  },
  methods: {
    addMovie() {
      this.$emit('add-movie', {
        image: this.image,
        title: this.title,
        year: this.year,
        rating: this.rating,
        description: this.description,
        comments: [],
        id: this.id,
      })
      this.id++
    },
    closeMenu() {
      this.$emit('close-menu')
    },
  },
}
</script>

<style scoped>
.form {
  padding: 40px 20px;
  background-color: rgba(182, 182, 182, 0.945);
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: left;
  margin: 10px auto;
  width: 600px;
  display: flex;
  flex-direction: column;
}
label {
  margin: 5px 0 10px;
}

input {
  font-size: 18px;
  padding: 12px 10px;
  margin-bottom: 10px;
}

textarea {
  font-size: 18px;
  padding: 12px 10px;
  height: 100px;
}

.button-block {
  display: flex;
  justify-content: center;
  margin: 15px 0 10px;
}

button {
  width: 110px;
  margin: 0 10px;
  font-size: 16px;
  padding: 12px 10px;
}
</style>
