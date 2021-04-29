<template>
  <div class="home">
    <!-- Intro -->
    <div id="intro">
      <h1>Stream-It</h1>
      <p>
        Don't know what to watch tonight? Enter some details about the kind of movie you're looking for and we'll make
        the perfect suggestion for you!
      </p>
      <ul class="actions">
        <li><a href="/signup" class="button icon solid solo fa-arrow-down scrolly">Continue</a></li>
      </ul>
      <!-- Main -->
      <div id="main">
        <!-- Featured Post -->
        <article class="post featured">
          <header class="major">
            <span class="date">MOVIE SUGGESTION</span>
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
                <input type="text" v-model="genre" placeholder="Genre" />
              </p>
              <a v-on:click="randomMovie()" class="button primary">Get Movie Suggestion</a>
              <h2>{{ final_movie.title }}</h2>
              <img v-bind:src="final_movie.image" />
              <p>{{ final_movie.plot }}</p>
              <p>{{ final_movie.year }}</p>
              <p>{{ final_movie.rating }}</p>
              <p>{{ final_movie.runtime_minutes }}</p>
              <p>{{ final_movie.media_type }}</p>
              <p>{{ final_movie.language }}</p>
              <p v-for="genre in final_movie.genres" v-bind:key="genre.name">{{ genre.name }}</p>
              <p v-for="network in final_movie.network" v-bind:key="network.name">{{ network.name }}</p>
              <a :href="final_movie.streaming_url" class="button primary">Watch Movie</a>
            </form>
            <a href="#" class="image main"><img v-bind:src="final_movie.image" alt="" /></a>
          </header>
        </article>
      </div>
    </div>
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
      streaming_url: "",
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
            year: this.year || null,
            rating: this.rating || null,
            media_type: this.media_type || null,
            language: this.language || null,
            runtime_minutes: this.runtime_minutes || null,
            genre: this.genre || null,
            network: this.network || null,
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
