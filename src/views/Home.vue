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

              Year:
              <input type="text" v-model="year" placeholder="Year" />
              Rating:
              <input type="text" v-model="rating" placeholder="Rating" />
              Length:
              <input type="text" v-model="runtime_minutes" placeholder="Length" />
              Type:
              <input type="text" v-model="media_type" placeholder="Type" />
              <div class="col-12">
                <select v-model="media_type">
                  <option value=""></option>
                  <option value="1">TV-Series</option>
                </select>
              </div>
              Language:
              <input type="text" v-model="language" placeholder="Language" />

              Network:
              <div class="col-12">
                <select v-model="network">
                  <option v-for="network in networks" v-bind:key="network.id">{{ network.name }}</option>
                </select>
              </div>

              Genre:
              <div class="col-12">
                <select v-model="genre">
                  <option value="">- Genres -</option>
                  <option v-for="genre in genres" v-bind:key="genre.id">{{ genre.name }}</option>
                </select>
              </div>
            </form>
            <a
              v-on:click="
                randomMovie();
                showMovie;
              "
              class="button primary"
            >
              Get Movie Suggestion
            </a>
            <div v-if="displayMovie">
              <h2>{{ final_movie.title }}</h2>
              <a href="#" class="image main"><img v-bind:src="final_movie.image" alt="" /></a>
              <!-- <div v-if="displayMovie"> -->
              <p>
                <!-- <b>Plot:</b> -->
                {{ final_movie.plot }}
              </p>
              <p>
                <!-- <b>Year:</b> -->
                {{ final_movie.year }}
              </p>
              <p>
                <!-- <b>Rating:</b> -->
                {{ final_movie.rating }}
              </p>
              <p>
                <!-- <b>Run-time:</b> -->
                {{ final_movie.runtime_minutes }}
                <!-- minutes -->
              </p>
              <p>
                <!-- <b>Type:</b> -->
                {{ final_movie.media_type }}
              </p>
              <p>
                <!-- <b>Language:</b> -->
                {{ final_movie.language }}
              </p>
              <p v-for="genre in final_movie.genres" v-bind:key="genre.name">
                <!-- <b>Genre:</b> -->
                {{ genre.name }}
              </p>
              <p v-for="network in final_movie.network" v-bind:key="network.name">
                <!-- <b>Network:</b> -->
                {{ network.name }}
              </p>
              <a v-if="displayMovie" :href="final_movie.streaming_url" class="button primary">Watch Movie</a>
              <!-- </div> -->
            </div>
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
      streaming_url: "",
      displayMovie: false,
      genres: [],
      networks: [],
      final_movie: {},
      errors: [],
    };
  },
  created: function () {
    // this.randomMovie();
    this.showMovie();
    axios.get(`api/genres`).then((response) => {
      console.log(response.data);
      this.genres = response.data;
    });
    axios.get(`api/networks`).then((response) => {
      console.log(response.data);
      this.networks = response.data;
    });
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
    showMovie: function () {
      // console.log("almost working");
      // if (this.displayMovie === true) {
      //   this.displayMovie = false;
      // } else {
      this.displayMovie = !this.displaySecret;
      // }
    },
  },
};
</script>
