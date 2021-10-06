<template>
  <div id="app">
    <Header @passInput="getQuery"/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {

    Header,
   
  },
  data() {
    return{
      passedInput: '',
      movies: []
      }
  },
  methods: {

    getQuery: function(inputValue){

      this.passedInput = inputValue;

      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '24da6980da0cf63e4d4cc8af46e62ed8',
          query: this.passedInput,
          language: 'it-IT'
        }
      })
      .then ((res) => {
        this.movies = res.data.results
        console.log(this.movies)
      })
    }
  }
  

}
</script>

<style lang="scss">
@import "./assets/style/common.scss";


</style>
