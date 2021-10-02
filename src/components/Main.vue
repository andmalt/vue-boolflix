<template>
  <main class="container-fluid">
    <div class="row">
      <div class="col-12 p-3" id="header">
        <div class="row">
          <div class="col-6">
            <a href="#"><img src="../assets/logo.png" alt="bootflix-font"></a>
          </div>

          <div class="col-6 d-flex justify-content-center align-items-center">
            <input type="text" placeholder="Search" v-model="searchBar">
            <button @click.prevent="search" class="btn-primary">search</button>
          </div>
        </div>
      </div>

      <div class="col-12 p-5" id="main-contain">
        <div class="row justify-content-center g-3">
          <div v-for="(element , index) in movie" :key="index" class="col-12 col-sm-6 col-lg-3 my-3">
            <div  class="card p-2">
              <ul>
                <li><img class="img-fluid poster mb-3" :src="filterImage(element.poster_path)" :alt="'poster '+ element.name"></li>
                <li><h5>Titolo: {{ element.title }}</h5></li>
                <li><p>Titolo originale: {{ element.original_title }}</p></li>
                <li>
                  <img v-if="element.original_language == 'it'" src="../assets/Italy.svg.png" alt="bandiera Italiana">
                  <img v-else-if="element.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="bandiera Regno Unito">
                </li>
                <li v-if="filterAverage(element.vote_average) == 1">
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 2">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 3">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 4">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 5">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
              </ul>
            </div>           
          </div>
        </div>
        <div class="row justify-content-center g-3">
          <div v-for="(element , index) in tv" :key="index" class="col-12 col-sm-6 col-lg-3 my-3">
            <div  class="card p-2">
              <ul>
                <li><img class="img-fluid poster mb-3" :src="filterImage(element.poster_path)" :alt="'poster '+ element.name"></li>
                <li><h5>Titolo: {{ element.name }}</h5></li>
                <li><p>Titolo originale: {{ element.original_name }}</p></li>
                <li>
                  <img v-if="element.original_language == 'it'" src="../assets/Italy.svg.png" alt="bandiera Italiana">
                  <img v-else-if="element.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="bandiera Regno Unito">
                </li>
                <li v-if="filterAverage(element.vote_average) == 1">
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 2">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 3">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 4">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li v-else-if="filterAverage(element.vote_average) == 5">
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
              </ul>
            </div>           
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Main',
  props: {
  },
  data(){
    return{
      searchBar:'',
      movie:[],
      tv:[],
      keyApi: '9d0595ce1c1db683468e3d616a3c1b98',
      image: 'https://image.tmdb.org/t/p/original/',
    }
  },
  methods:{
    search(){
      axios.get('https://api.themoviedb.org/3/search/movie?', {
          params: {
            api_key: this.keyApi,
            query: this.searchBar,
          } 
        })
        .then((res)=> {
          this.movie = [...res.data.results];
          console.log(this.movie);
      });
      axios.get('https://api.themoviedb.org/3/search/tv?', {
          params: {
            api_key: this.keyApi,
            query: this.searchBar,
          } 
        })
        .then((res)=> {
          this.tv = [...res.data.results];
          console.log(this.tv);
      });
    },
    filterImage(element){
      return this.image + element;
    },
    filterAverage(element){
      return parseInt(element / 2);
    }
  },
  computed:{

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../style/general.scss';

#header{
  background-color: black;
}
#main-contain{
  background-color: gray;
}
.card{
  background-color: black;
  color: white;
  height: 38rem;
  & img{
    width: 25px;
  }
  & ul{
    list-style: none;
    padding: 0;

    & li{
      margin: 0.5rem;
      
      .poster{
        width: 80%;
      }
    }
  }
}


</style>
