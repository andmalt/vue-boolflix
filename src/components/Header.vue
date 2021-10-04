<template>
<div class="container-fluid">
    <div class="row">
        <div class="col-12 p-3" id="header">
        <div class="row">
          <div class="col-12 col-md-6 col-lg-6">
            <a href="#"><img src="../assets/logo.png" alt="bootflix-font"></a>
          </div>

          <div class="col-12 col-md-6 col-lg-6 d-flex justify-content-center align-items-center">
            <input type="text" placeholder="Search" v-model="searchBar">
            <button @click.prevent="$emit('search', searchBar)" class="btn-primary">search</button>
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
    }

  },
}
</script>

<style>
@import '../style/general.scss';

#header{
  background-color: black;
}
</style>