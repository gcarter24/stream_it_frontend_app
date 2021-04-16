<template>
  <div class="movies-random">
    <h1>{{ message }}</h1>
    <form>
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
        <input type="text" v-model="genre" placeholder="Genre" />
      </p>
      <button v-on:click="randomMovie()">Any Random Movie</button>
      <p>{{ final_movie.title }}</p>
      <img v-bind:src="final_movie.image" />
      <p>{{ final_movie.plot }}</p>
      <p>{{ final_movie.year }}</p>
      <p>{{ final_movie.rating }}</p>
      <p>{{ final_movie.runtime_minutes }}</p>
      <p>{{ final_movie.media_type }}</p>
      <p>{{ final_movie.language }}</p>
      <p>
        {{ final_movie.genre }}
      </p>
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
      message: "Welcome to Random!",
      year: "2021",
      rating: "R",
      media_type: "movie",
      language: "English",
      runtime_minutes: "242",
      genre: "Action",
      network: "HBO Max",
      final_movie: {},
    };
  },
  created: function () {},
  methods: {
    randomMovie: function () {
      console.log("in random");
      var params = {
        year: this.year,
        rating: this.rating,
        media_type: this.media_type,
        language: this.language,
        runtime_minutes: this.runtime_minutes,
        genre: this.genre,
        network: this.network,
      };
      axios.get("/api/movies/random", params).then((response) => {
        console.log(response.data);
        this.final_movie = response.data;
      });
    },
  },
};
</script>
