<template>
  <div id="app">
    <Header @search="search" @lang="changeLanguage" />
    <Main :movies="movie" :series="tv" :tcast="tvCast" :mcast="movieCast"  />
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
      lang:'',
      movieCast:[],
      tvCast:[],
      movie:[],
      tv:[],
      keyApi: '9d0595ce1c1db683468e3d616a3c1b98',
      getMovie:'https://api.themoviedb.org/3/search/movie?', 
      getTv:'https://api.themoviedb.org/3/search/tv?',
    }
  },
  methods:{
    changeLanguage(el){
      this.lang = el;
    },
    search(el){
      // get movie
      axios.get(this.getMovie, {
          params: {
            api_key: this.keyApi,
            query: el,
            language:this.lang
          } 
        })
        .then((res)=> {
          this.movie = [...res.data.results];
          // console.log(this.movie);
        });
      // get tv series
        axios.get(this.getTv, {
          params: {
            api_key: this.keyApi,
            query: el,
            language:this.lang
          } 
        })
        .then((res)=> {
          this.tv = [...res.data.results];
          // console.log(this.tv);
        });
        setTimeout(this.getCast ,200);
        
    },
    getCast(){
      this.movie.forEach((element)=>{
        // get movie cast
      axios.get(`https://api.themoviedb.org/3/movie/${element.id}/credits?`, {
          params: {
            api_key: this.keyApi,
            language:this.lang,
          } 
        })
        .then((res)=> {
          // console.log(res.data.cast);
          this.movieCast.push(res.data.cast);
        });
      })
      console.log(this.movieCast);
      this.tv.forEach((element)=>{
        // get tv cast
      axios.get(`https://api.themoviedb.org/3/tv/${element.id}/credits?`, {
          params: {
            api_key: this.keyApi,
            language:this.lang,
          } 
        })
        .then((res)=> {
          // console.log(res.data.cast);
          this.tvCast.push(res.data.cast);
          
        });
      })
      console.log(this.tvCast);
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
