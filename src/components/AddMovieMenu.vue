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
    <div class="error" v-if="errorMsg.length > 0">{{ errorMsg }}</div>
  </div>
</template>

<script>
export default {
  name: 'addMovieMenu',
  watch: {},
  data() {
    return {
      errorMsg: '',
      image: '',
      title: '',
      year: '',
      rating: '',
      description: '',
      id: 7,
    }
  },
  methods: {
    addMovie() {
      if (this.formFill() === true) {
        let strId = this.id.toString()
        this.$emit('add-movie', {
          image: this.image,
          title: this.title,
          year: this.year,
          rating: this.rating,
          description: this.description,
          comments: [],
          id: strId,
        })
        ++this.id
      }
    },
    formFill() {
      if (
        this.image.length > 0 &&
        this.title.length > 0 &&
        this.year.length > 0 &&
        this.rating.length > 0 &&
        this.description.length > 0
      ) {
        this.errorMsg = ''
        return true
      } else {
        return (this.errorMsg = 'Please fill the form')
      }
    },
    closeMenu() {
      this.$emit('close-menu')
    },
  },
}
</script>

<style scoped>
.form {
  border-radius: 8px;
  padding: 45px 45px;
  background-color: #f0f0f0;
  box-shadow: 0px 10px 15px 0px rgba(50, 50, 50, 0.5);
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: left;
  margin: 10px auto;
  width: 500px;
  display: flex;
  flex-direction: column;
}
label {
  color: #0c3f3b;
  margin: 10px 3px 5px;
}

input {
  background: none;
  border-radius: 4px;
  border: 2px solid #157970;
  outline: none;
  color: #0c3f3b;
  font-size: 18px;
  padding: 12px 10px;
  margin-bottom: 10px;
}

textarea {
  outline: none;
  resize: none;
  border-radius: 4px;
  border: 2px solid #157970;
  background: none;
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
  outline: none;
  font-size: 18px;
  font-weight: 600;
  border-radius: 4px;
  color: #157970;
  border-radius: 4px;
  border: 2px solid #157970;
  width: 130px;
  margin: 10px 10px;
  padding: 12px 10px;
}

.error {
  text-align: center;
  color: #791c15;
}
</style>
