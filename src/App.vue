<template>
  <div id="app">
    <Header 
      @searchTitle="startSearch"
      @resetInput=" searchMovies = [], searchSeries = []"
    />
    <Main 
      :searchMoviesList="searchMovies"
      :searchSeriesList="searchSeries"
    />
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/js/all.js';

import Header from './components/Header.vue'
import Main from './components/Main.vue'

import axios from 'axios'


export default {
  name: 'App',

  components: {
    Header,
    Main
  },
  data(){
    return {
      searchText:'',
      searchMovies: [],
      searchSeries: [],
    }
  },
  methods: {
    getApiList(){
          axios.get('https://api.themoviedb.org/3/search/movie?api_key=82b3378dac0b800eb4daa7c5da96f82b&query='+ this.searchText)
          
          .then((result) => {
              this.searchMovies = result.data.results;
            })
          .catch((error) => {
              console.log(error);
          })
          
          axios.get('https://api.themoviedb.org/3/search/tv?api_key=82b3378dac0b800eb4daa7c5da96f82b&query='+ this.searchText)
          
          .then((result) => {
              this.searchSeries = result.data.results;
            })
          .catch((error) => {
              console.log(error);
          })
      },

      startSearch(searchInput){
        this.searchText = searchInput;
        this.getApiList();
      },
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap');
  @import "./src/styles/style.scss";
  </style>