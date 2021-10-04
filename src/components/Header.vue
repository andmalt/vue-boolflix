<template>
<div class="container-fluid">
    <div class="row">
        <div class="col-12 p-3" id="header">
        <div class="row">
          <div class="col-12 col-md-6 col-lg-6">
            <a href="#"><img src="../assets/logo.png" alt="bootflix-font"></a>
          </div>

          <div class="col-12 col-md-6 col-lg-6 d-flex justify-content-center align-items-center">
            <input type="text" placeholder="Search" v-model="searchBar" class="p-1">
            <button @click.prevent="$emit('search', searchBar)" class="btn-danger btn_red rounded-end p-1">search</button>
            <div class="flag_l ms-5">
              <button class="flagl" @click.prevent="$emit('lang', langIt)"><img  src="../assets/Italy.svg.png" alt="Italy flag"></button>
              <button class="flagl" @click.prevent="$emit('lang', langEn)"><img  src="../assets/United_Kingdom.svg.png" alt="Uk flag"></button>                        
            </div>
          </div>
        </div>
      </div>
    </div>
</div>

</template>

<script>


export default {
  name:'Header',
  data(){
    return{
        searchBar:'',
        langEn: 'en',
        langIt: 'it',
    }

  },
  methods:{
    
  }
}
</script>

<style scope lang="scss">
@import '../style/general.scss';

#header{
  background-color: black;
  
  .btn_red{
  color: black;
  }
  .flag_l{
    img{
      height: 20px;
      margin-right: 0.5rem;
    }
  }
  .flagl{
    border: none;
    background-color: black;
  }
}

</style>