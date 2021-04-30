<template>
  <div class="movies-show">
    <header id="header">
      <a href="/" class="logo">Homepage</a>
    </header>
    <!-- Main -->
    <div id="main">
      <div class="field">
        <label for="title">Search Titles</label>
        <input type="text" v-model="title" placeholder="Search" />
        <a v-on:click="movieTitle()" class="button primary">Search for Title</a>
      </div>

      <!-- Featured Post -->
      <article class="post featured">
        <header class="major">
          <span class="date">Featured Movie</span>
          <h1>{{ message }}</h1>
          <!-- <p>
      <b>Id:</b>
      {{ movie.id }}
    </p> -->

          <p>
            <b>Title:</b>
            {{ movie.title }}
          </p>
          <p>
            <a href="#" class="image main"><img v-bind:src="movie.image" alt="" /></a>
          </p>
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
          <p v-for="genre in movie.genres" v-bind:key="genre.name">
            <b>Genre:</b>
            {{ genre.name }}
          </p>
          <p>
            <b>Network:</b>
            {{ movie.network }}
          </p>
          <a :href="movie.streaming_url" class="button primary">Watch Movie</a>
        </header>

        <ul class="actions special"></ul>
      </article>

      <!-- Posts -->
      <!-- <section class="posts">
        <article>
          <header>
            <span class="date">April 24, 2017</span>
            <h2>
              <a href="#">
                Sed magna
                <br />
                ipsum faucibus
              </a>
            </h2>
          </header>
          <a href="#" class="image fit"><img src="images/pic02.jpg" alt="" /></a>
          <p>
            Donec eget ex magna. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque venenatis
            dolor imperdiet dolor mattis sagittis magna etiam.
          </p>
          <ul class="actions special">
            <li><a href="#" class="button">Full Story</a></li>
          </ul>
        </article>
        <article>
          <header>
            <span class="date">April 22, 2017</span>
            <h2>
              <a href="#">
                Primis eget
                <br />
                imperdiet lorem
              </a>
            </h2>
          </header>
          <a href="#" class="image fit"><img src="images/pic03.jpg" alt="" /></a>
          <p>
            Donec eget ex magna. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque venenatis
            dolor imperdiet dolor mattis sagittis magna etiam.
          </p>
          <ul class="actions special">
            <li><a href="#" class="button">Full Story</a></li>
          </ul>
        </article>
      </section> -->
    </div>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      title: "",
      message: "Movie Description",
      movie: {},
    };
  },
  created: function () {
    // console.log(this.$route.params.id);
    // axios.get(`/api/movies/${this.$route.params.id}`).then((response) => {
    //   console.log(response.data);
    //   this.movie = response.data;
    // });
    // this.movieTitle();
  },
  methods: {
    movieTitle: function () {
      axios.get(`/api/movies/36`).then((response) => {
        console.log(response.data);
        this.movie = response.data;
      });
    },
  },
};
</script>
