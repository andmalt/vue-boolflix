<template>
  <main class="container-fluid">
    <div class="row">

      <div class="col-12 p-5" id="main-contain">
        <div class="row justify-content-center g-3">
          <div v-for="(element , index) in movies" :key="index" class="col-12 col-sm-6 col-lg-3 my-3">
            <div  class="card p-4 d-flex">
              <ul>
                <li><img class="img-fluid poster mb-3" :src="filterImage(element.poster_path)" :alt="'poster '+ element.name"></li>
                <li><h5>Titolo: {{ element.title }}</h5></li>
                <li><p>Titolo originale: {{ element.original_title }}</p></li>
                <li>
                  <img v-if="element.original_language == 'it'" src="../assets/Italy.svg.png" alt="bandiera Italiana">
                  <img v-else-if="element.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="bandiera Regno Unito">
                </li>
                <li class="d-flex align-items-center" v-if="filterAverage(element.vote_average) == 1">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 2">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 3">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 4">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 5">
                  <p><strong>Voto: </strong></p>
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
          <div v-for="(element , index) in series" :key="index" class="col-12 col-sm-6 col-lg-3 my-3">


            <!-- <div class="card">
              <img class="img-fluid poster" :src="filterImage(element.poster_path)" :alt="'poster '+ element.name">
            </div>  -->

            <div  class="card p-4 d-flex">
              <ul>
                <li><img class="img-fluid poster mb-3" :src="filterImage(element.poster_path)" :alt="'poster '+ element.name"></li>
                <li><h5>Titolo: {{ element.name }}</h5></li>
                <li><p>Titolo originale: {{ element.original_name }}</p></li>
                <li>
                  <img v-if="element.original_language == 'it'" src="../assets/Italy.svg.png" alt="bandiera Italiana">
                  <img v-else-if="element.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="bandiera Regno Unito">
                </li>
                <li class="d-flex align-items-center" v-if="filterAverage(element.vote_average) == 1">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 2">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 3">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 4">
                  <p><strong>Voto: </strong></p>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                  <i  class="fas fa-star"></i>
                </li>
                <li class="d-flex align-items-center" v-else-if="filterAverage(element.vote_average) == 5">
                  <p><strong>Voto: </strong></p>
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

export default {
  name: 'Main',
  props: {
    movies:Array,
    series:Array,
  },
  data(){
    return{
      image: 'https://image.tmdb.org/t/p/original/',
    }
  },
  methods:{
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

#main-contain{
  background-color: gray;
  min-height: calc(100vh - 118px);
}
.card{
  background-color: black;
  color: white;
  height: 40rem;
  & img{
    width: 25px;
  }
  & ul{
    list-style: none;
    padding: 0;

    & li{
      margin: 0.5rem;
      
      & p{
        margin: 0;
        margin-right: 0.6rem;
      }
      .poster{
        width: 100%;
      }
    }
  }
}


</style>
