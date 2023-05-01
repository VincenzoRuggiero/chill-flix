<script>
import { store } from "../store.js";
import MovieTvShow from "./MovieTvShow.vue";

export default {
  name: "AppMain",

  components: {
    MovieTvShow,
  },

  data() {
    return {
      store,
      posterPath: "https://image.tmdb.org/t/p/w342/",
    };
  },

  methods: {
    getImagePath: function (imgPath) {
      return new URL(`../assets/img/${imgPath}.png`, import.meta.url).href;
    },
  },

  created() {},
};
</script>

<template>
  <main>
    <div class="container">
      <section
        class="no-content"
        v-show="(store.movieList.length || store.tvShows.length) === 0">
        <h1>I risultati della ricerca appariranno qui</h1>
      </section>

      <section class="movies">
        <h1 v-show="store.movieList.length > 0">
          Film trovati: {{ store.movieList.length }}
        </h1>

        <div class="wrapper-card flex">
          <MovieTvShow
            v-for="movie in store.movieList"
            :originalTitle="movie.original_title"
            :title="movie.title"
            :star="movie.vote_average"
            :image="posterPath + movie.poster_path"
            :language="getImagePath(movie.original_language)" />
        </div>
      </section>

      <section class="tv-shows">
        <h1 v-show="store.tvShows.length > 0">
          Serie Tv trovate: {{ store.tvShows.length }}
        </h1>

        <div class="wrapper-card flex">
          <MovieTvShow
            v-for="tvShow in store.tvShows"
            :originalTitle="tvShow.original_name"
            :star="tvShow.vote_average"
            :image="posterPath + tvShow.poster_path"
            :language="tvShow.original_language"
            :title="tvShow.name" />
        </div>
      </section>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  padding-top: 4rem;

  h1 {
    color: grey;
    font-size: 3rem;
    text-align: center;
    margin: 3rem 0;
  }

  .wrapper-card {
    flex-wrap: wrap;
    margin-bottom: 2rem;
  }
}
</style>
