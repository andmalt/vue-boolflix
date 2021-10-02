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
          <div v-for="(element , index) in movie" :key="index" class="col-12 col-sm-6 col-lg-2 my-3">
            <div class="card">
              <h5>Titolo: {{ element.title}}</h5>
              <p>Titolo originale: {{ element.original_title }}</p>

              <p>Lingua: {{element.original_language}}</p>
              <p>Voto: {{ element.vote_average }}</p>
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
      keyApi: '9d0595ce1c1db683468e3d616a3c1b98',
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
    },
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
}

</style>
