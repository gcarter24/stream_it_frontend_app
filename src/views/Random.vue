<template>
  <div class="movies-random">
    <h1>{{ message }}</h1>
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
    <button v-on:click="anyRandomMovie()">Any Random Movie</button>
    <p>{{ randomMovie.title }}</p>
    <img v-bind:src="randomMovie.image" />
    <p>{{ randomMovie.plot }}</p>
    <p>{{ randomMovie.year }}</p>
    <p>{{ randomMovie.rating }}</p>
    <p>{{ randomMovie.runtime_minutes }}</p>
    <p>{{ randomMovie.media_type }}</p>
    <p>{{ randomMovie.language }}</p>
    <p>
      {{ randomMovie.genre }}
    </p>
    <p>{{ randomMovie.network }}</p>
    <!-- <p>
      <b>Title:</b>
      {{ movie.title }}
    </p>
    <p><img v-bind:src="movie.image" /></p>
    <p>
      <b>Plot:</b>
      {{ movie.plot }}
    </p>
    <p>
      <b>Year:</b>
      {{ movie.year }}
    </p>
    <p>
      <b>Rating:</b>
      {{ movie.rating }}
    </p>
    <p>
      <b>Run-time:</b>
      {{ movie.runtime_minutes }} minutes
    </p>
    <p>
      <b>Type:</b>
      {{ movie.media_type }}
    </p>
    <p>
      <b>Language:</b>
      {{ movie.language }}
    </p>
    <p>
      <b>Genres:</b>
      {{ movie.genres }}
    </p>
    <p>
      <b>Network:</b>
      {{ movie.network }}
    </p> -->
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to the Random Page!",
      year: "",
      rating: "",
      runtime_minutes: "",
      media_type: "",
      language: "",
      network: "",
      genre: "",
      randomMovie: {},
      movie: {},
    };
  },
  created: function () {},
  methods: {
    anyRandomMovie: function () {
      var params = {
        year: this.year,
        rating: this.rating,
        runtime_minutes: this.runtime_minutes,
        media_type: this.media_type,
        language: this.language,
        network: this.network,
        genres: this.genre,
      };
      axios.get("/api/movies/random", params).then((response) => {
        console.log(response.data);
        this.randomMovie = response.data;
      });
    },
  },
};
</script>
