<template>
  <div id="app">
    <Header @search="search" />
    <Main :movies="movie" :series="tv" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
      movie:[],
      tv:[],
      keyApi: '9d0595ce1c1db683468e3d616a3c1b98',
    }
  },
  methods:{
    search(el){
      axios.get('https://api.themoviedb.org/3/search/movie?', {
          params: {
            api_key: this.keyApi,
            query: el,
          } 
        })
        .then((res)=> {
          this.movie = [...res.data.results];
          console.log(this.movie);
      });
      axios.get('https://api.themoviedb.org/3/search/tv?', {
          params: {
            api_key: this.keyApi,
            query: el,
          } 
        })
        .then((res)=> {
          this.tv = [...res.data.results];
          console.log(this.tv);
      });
    },
  },

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
