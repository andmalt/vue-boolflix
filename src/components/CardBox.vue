<template>
  <div @mouseover="hover = true" @mouseleave="hover = false" class="col-12 col-sm-6 col-md-4 col-lg-3 col-xxl-2 my-3">
        <div  v-if="hover == false"  class="card-img p-3 ">
            <img class="img-fluid poster" :src="filterImage(movie.poster_path)" :alt="'poster '+ movie.name">
        </div> 

        <div v-if="hover" class="card text-start p-3 d-flex">
            <ul>
                <li>
                    <h5> <strong>Title:</strong> {{ movie.title ? movie.title : movie.name }}</h5>
                </li>
                <li>
                    <h6> <strong>Original title:</strong> {{ movie.original_title ? movie.title : movie.name }} </h6>
                </li>
                <li>
                    <img v-if="movie.original_language == 'it'" src="../assets/Italy.svg.png" alt="bandiera Italiana">
                    <img v-else-if="movie.original_language == 'en'" src="../assets/United_Kingdom.svg.png" alt="bandiera Regno Unito">
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
            </ul>
        </div>
  </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        movie:Object,
        serie:Object,
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
    }
  }
  & .fa-star{
    color: goldenrod;
  }
}
.card-img{
  height: 350px;
  background-color: black;
  

  & img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
}
</style>