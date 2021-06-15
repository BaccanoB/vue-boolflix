<template>
  <div id="app">
    <Header @userResearch='newQuery' />
    <Main :search="allResults"/>
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
        api_key: '838b4a196c57a8cffba225213ba6f953',
        query: 'ritorno',
        language: 'it-IT'
      },
      movies: [],
      series:[],
      allResults:[]
    }
  },
  methods: {
      getMovies() {
        axios
           .get('https://api.themoviedb.org/3/search/movie', {
             params: this.params
           })
            .then((res) => {
              this.movies = res.data.results;
              console.log('film',this.movies);
              this.allResults=this.movies.concat(this.series)
            })
        },
      getSeries(){
         axios
           .get('https://api.themoviedb.org/3/search/tv', {
             params: this.params
           })
           .then((res) => {
              this.series = res.data.results;
              console.log('series',this.series);
              this.allResults=this.series.concat(this.movies)
            })
      },
      newQuery(text){
        this.params.query=text;
        this.getMovies();
        this.getSeries();
      }
  }
}
</script>

<style lang="scss">
  @import './style/general';

</style>
