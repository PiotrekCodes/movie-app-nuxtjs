<template>
  <div class="home">
    <HeroComp />
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  data() {
    return {
      movies: [],
    }
  },
  async fetch() {
    await this.getMovies()
  },
  methods: {
    async getMovies() {
      const data = axios.get(
        ' https://api.themoviedb.org/3/movie/popular?api_key=8dfdd79ea5a39d1f1a4e614aa46fa1f7&language=en-US&page=1'
      )
      const result = await data
      result.data.results.forEach((movie) => {
        this.movies.push(movie)
      })
      console.log(this.movies)
    },
  },
}
</script>
