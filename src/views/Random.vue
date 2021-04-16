<template>
  <div class="movies-random">
    <h1>{{ message }}</h1>
    <!-- <p>
      <b>Id:</b>
      {{ movie.id }}
    </p> -->

    <form>
      <div class="form-group">
        <label>Year:</label>
        <input type="text" class="form-control" v-model="movie.year" />
      </div>
      <div class="form-group">
        <label>Rating:</label>
        <input type="text" class="form-control" v-model="movie.rating" />
      </div>
      <div class="form-group">
        <label>Run-time:</label>
        <input type="text" class="form-control" v-model="movie.runtime_minutes" />
      </div>
      <div class="form-group">
        <label>Type:</label>
        <input type="text" class="form-control" v-model="movie.media_type" />
      </div>
      <div class="form-group">
        <label>Language:</label>
        <input type="text" class="form-control" v-model="movie.language" />
      </div>
      <div class="form-group">
        <label>Genre:</label>
        <input type="text" class="form-control" v-model="movie.genre" />
      </div>
      <div class="form-group">
        <label>Network:</label>
        <input type="text" class="form-control" v-model="movie.network" />
      </div>
      <input type="submit" class="btn btn-primary" value="Any Random Movie" />
    </form>
    <p>{{ movie.title }}</p>
    <img v-bind:src="movie.image" />
    <p>{{ movie.plot }}</p>
    <p>{{ movie.year }}</p>
    <p>{{ movie.rating }}</p>
    <p>{{ movie.runtime_minutes }}</p>
    <p>{{ movie.media_type }}</p>
    <p>{{ movie.language }}</p>
    <p>
      {{ movie.genre }}
    </p>
    <p>{{ movie.network }}</p>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Random!",
      title: "",
      movie: {},
    };
  },
  created: function () {
    console.log(this.$route.params.id);
    axios.get(`/api/movies/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.movie = response.data;
    });
  },
  methods: {
    randomMovie: function () {
      var params = {
        title: this.title,
        plot: this.plot,
        media_type: this.media_type,
        runtime_minutes: this.runtime_minutes,
        year: this.year,
        rating: this.rating,
        language: this.language,
      };
      axios.get("/api/movies/random", params).then((response) => {
        console.log(response.data);
      });
    },
  },
};
</script>
