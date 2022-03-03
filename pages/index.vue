<template>
  <div class="home">
    <Hero />
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      movies: [],
    };
  },
  async fetch() {
    await this.getMovies();
  },
  methods: {
    async getMovies() {
      const data = axios.get(
        "https://anime-facts-rest-api.herokuapp.com/api/v1"
      );
      const result = await data;

      result.data.data.forEach((movie) => {
        this.movies.push(movie);
      });
      console.log(this.movies);
    },
  },
};
</script>
