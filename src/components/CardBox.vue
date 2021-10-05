<template>
  <div @mouseover="hover = true" @mouseleave="hover = false" class="col-12 col-sm-6 col-md-4 col-lg-3 col-xxl-2 my-3">
        <div  v-if="hover == false"  class="card-img p-1 ">
            <img v-if="movie.poster_path != null" class="img-fluid" :src="filterImage(movie.poster_path)" :alt="'poster '+ movie.title? movie.title : movie.name ">
            <img v-else src="" class="img-fluid poster" alt="">
        </div> 

        <div v-else-if="hover" class="card text-start px-2 py-3 d-flex">
            <ul>
              <li>
                <h5> <strong>TITLE:</strong> {{ movie.title ? movie.title : movie.name }}</h5>
              </li>
              <li>
                <h6> <strong>Oiginal title:</strong> {{ movie.original_title ? movie.original_title : movie.original_name }} </h6>
              </li>
              <li>
                <p><strong>Original language: </strong>
                  <img v-if="movie.original_language == 'it'" src="../assets/Italy.svg.png" alt="italian flag">
                  <img v-else-if="movie.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="UK flag">
                </p>               
              </li>
              <li>
                <p><strong>Genre: </strong>{{ movie.title ? 'Movie' : 'Tv series' }}</p>
              </li>
              <li class="d-flex align-items-center" v-if="filterAverage(movie.vote_average) == 1">
                <p><strong>Average: </strong></p>
                <i  class="fas fa-star"></i>
              </li>
              <li class="d-flex align-items-center" v-else-if="filterAverage(movie.vote_average) == 2">
                <p><strong>Average: </strong></p>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
              </li>
              <li class="d-flex align-items-center" v-else-if="filterAverage(movie.vote_average) == 3">
                <p><strong>Average: </strong></p>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
              </li>
              <li class="d-flex align-items-center" v-else-if="filterAverage(movie.vote_average) == 4">
                <p><strong>Average: </strong></p>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
              </li>
              <li class="d-flex align-items-center" v-else-if="filterAverage(movie.vote_average) == 5">
                <p><strong>Average: </strong></p>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
                <i  class="fas fa-star"></i>
              </li>
              <li>
                <p><strong>Overview: </strong> <em>{{ movie.overview }}</em></p>
              </li>
              <!-- <li>
                <h6><strong>Cast:</strong></h6>
                <p > {{ cast.original_name }} <strong>alias</strong> {{ cast.character }}</p>
              </li> -->
            </ul>
        </div>
  </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        movie:Object,
        cast:Object,

    },
    data(){
    return{
      image: 'https://image.tmdb.org/t/p/original/',
      hover:false,
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
}
</script>

<style lang="scss">
@import '../style/general.scss';



.card{
  background-color: black;
  color: white;
  height: 350px;
  overflow: auto;
  strong{
    color: rgb(209, 39, 39);
  }
  & img{
    width: 25px;
  }
  & ul{
    list-style: none;
    padding: 0;

    & li{
      margin: 0.6rem;
      
      & p{
        margin: 0;
        margin-right: 0.6rem;
      }
    }
  }
  & .fa-star{
    color: goldenrod;
  }
}
.card-img{
  height: 350px;
  background-color: black;
  
  .poster{
    background-color: rgb(214, 48, 48);
    padding: 0.5rem;
  }

  & img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
}
</style>