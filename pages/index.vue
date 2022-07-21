<template>
  <div class="home">
    <HeroBanner />
  </div>
</template>

<script>
import axios from 'axios'
import HeroBanner from '../components/HeroBanner.vue';

export default {
    name: "IndexPage",
    components: { HeroBanner },
    data() {
      return {
        movies: []
      }
    },

    async fetch() {
      await this.getMovies();
    },

    methods: {
      async getMovies() {
        const data = axios.get('https://api.themoviedb.org/3/movie/now_playing?api_key=8110ad422ce97b0ac68b9df44e276ba5&language=en-US&page=1');
        const result = await data;

        result.data.results.forEach((movie) => {
          this.movies.push(movie)
        })
        console.log(this.movies)
      }
    }
}
</script>
