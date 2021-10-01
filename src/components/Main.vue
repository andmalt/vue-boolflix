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
            <button @click="search" class="btn-primary">search</button>
          </div>
        </div>
      </div>

      <div class="col-12" id="main-contain">

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
      results:[],
    }
  },
  methods:{
    search(){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=9d0595ce1c1db683468e3d616a3c1b98&query=lo+squalo')
        .then(res => {
        this.results = res.data.results.slice();
        console.log(this.results);
      });
      // this.searchBar = element;
      console.log(this.searchBar);
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


</style>
