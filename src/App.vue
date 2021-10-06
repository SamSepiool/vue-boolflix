<template>
  <div id="app">
    <Header @passInput="getQuery"/>
    <Films :movies='movies'/>
    <Series :tvSeries='tvSeries'/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Films from "./components/Films.vue";
import Series from "./components/Series.vue";


import axios from "axios";


export default {
  name: 'App',
  components: {

    Header,
    Films,
    Series ,

   
  },
  data() {
    return{
      passedInput: '',
      movies: [],
      tvSeries: []
      }
  },
  methods: {

    getQuery: function(inputValue){

      if (inputValue == '') {
        this.movies = []
        this.tvSeries = []
      } else {

        this.passedInput = inputValue;
        
        // MOVIES API CALL
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

        // SERIES API CALL 
        axios.get('https://api.themoviedb.org/3/search/tv', {
          params: {
            api_key: '24da6980da0cf63e4d4cc8af46e62ed8',
            query: this.passedInput,
            language: 'it-IT'
          }
          })
          .then ((res) => {
            this.tvSeries = res.data.results
            console.log(this.tvSeries)
        })
      } 
    }
  }
}
</script>

<style lang="scss">
@import "./assets/style/common.scss";





</style>
