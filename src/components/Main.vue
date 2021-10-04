<template>
  <main class="container-fluid">
    <div class="row">

      <div class="col-12 p-5" id="main-contain">
        <!-- film -->
        <div class="row justify-content-center g-3">
          <Cards :movie="movie" v-for="(movie , index) in movies" :key="index" />
        </div>
        <!-- series -->
        <div class="row justify-content-center g-3" >
          <Cards :movie="serie" v-for="(serie , index) in series" :key="index" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Cards from './CardBox.vue';

export default {
  name: 'Main',
  components:{
    Cards,
  },
  props: {
    movies:Array,
    series:Array,
  },
  data(){
    return{

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

</style>
