<template>
  <main class="container-fluid">
    <div class="row">

      <div class="col-12 p-5" id="main-contain">
        <!-- Movies and Tv series -->
        <div class="row g-3">
          <Cards :movie="movie"  v-for="movie in movies" :key="movie.id" />
          <Cards :movie="serie"  v-for="serie in series" :key="serie.id" />
          <!-- <Cards :cast="castm" v-for="(castm , index ) in mcast" :key="index" />
          <Cards :cast="castt" v-for="(castt , index ) in tcast" :key="index" /> -->
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
    tcast:Array,
    mcast:Array,
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
  background-color: rgba(133, 133, 133, 0.7);
  min-height: calc(100vh - 118px);
}

</style>
