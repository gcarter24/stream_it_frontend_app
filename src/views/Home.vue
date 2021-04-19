<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <form v-on:submit.prevent="randomMovie()">
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <p>
        Year:
        <input type="text" v-model="year" placeholder="Year" />
        Rating:
        <input type="text" v-model="rating" placeholder="Rating" />
        Length:
        <input type="text" v-model="runtime_minutes" placeholder="Length" />
        Type:
        <input type="text" v-model="media_type" placeholder="Type" />
        Language:
        <input type="text" v-model="language" placeholder="Language" />
        Network:
        <input type="text" v-model="network" placeholder="Network" />
        Genre:
        <!-- <li v-for="genre in genres" :key="genre.name">
          {{ genre.name }}
        </li> -->
        <input type="text" v-model="genre" placeholder="Genre" />
      </p>
      <a v-on:click="randomMovie()" class="button primary">Any Random Movie</a>
      <p>{{ final_movie.title }}</p>
      <img v-bind:src="final_movie.image" />
      <p>{{ final_movie.plot }}</p>
      <p>{{ final_movie.year }}</p>
      <p>{{ final_movie.rating }}</p>
      <p>{{ final_movie.runtime_minutes }}</p>
      <p>{{ final_movie.media_type }}</p>
      <p>{{ final_movie.language }}</p>
      <p>{{ final_movie.genres }}</p>
      <p>{{ final_movie.network }}</p>
    </form>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      year: "",
      rating: "",
      media_type: "",
      language: "",
      runtime_minutes: "",
      genre: "",
      network: "",
      final_movie: {},
      errors: [],
    };
  },
  created: function () {
    this.randomMovie();
  },
  methods: {
    randomMovie: function () {
      console.log("homepage in randomMovie");

      axios
        .get("/api/movies/random", {
          params: {
            year: this.year,
            rating: this.rating,
            media_type: this.media_type,
            language: this.language,
            runtime_minutes: this.runtime_minutes,
            genre: this.genre,
            network: this.network,
          },
        })
        .then((response) => {
          console.log(response.data);
          this.final_movie = response.data;
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
