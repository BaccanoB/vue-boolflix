<template>
  <div id="app">
    <Header @userResearch='newQuery' />
    <Main :movies="movies" />
  </div>
</template>

<script>
import axios from'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      params:{
        url:'https://api.themoviedb.org/3/search/movie',
        api_key: '838b4a196c57a8cffba225213ba6f953',
        query: 'ritorno',
        language: 'it-IT'
      },
      movies: []
    }
  },
  methods: {
      getMovies() {
        axios
           .get(this.params.url, {
             params: this.params
           })
            .then((res) => {
              this.movies = res.data.results;
              console.log(this.movies);
            })
        },
      newQuery(text){
        this.params.query=text;
        this.getMovies();
      }
  }
}
</script>

<style lang="scss">
  @import './style/general';

</style>
