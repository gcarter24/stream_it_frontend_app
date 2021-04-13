<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <button v-on:click="movieRandom()">Random Movie</button>
    <p>{{ randomMovie.title }}</p>
    <img v-bind:src="randomMovie.image" />
    <p>{{ randomMovie.plot }}</p>
    <p>{{ randomMovie.year }}</p>
    <p>{{ randomMovie.rating }}</p>
    <p>{{ randomMovie.runtime_minutes }}</p>
    <p>{{ randomMovie.media_type }}</p>
    <p>{{ randomMovie.language }}</p>
    <p>{{ randomMovie.genres }}</p>
    <p>{{ randomMovie.network }}</p>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Stream-It",
      randomMovie: {},
    };
  },
  created: function () {},
  methods: {
    movieRandom: function () {
      axios.get("/api/movies/random").then((response) => {
        console.log(response.data);
        this.randomMovie = response.data;
      });
    },
  },
};
</script>
