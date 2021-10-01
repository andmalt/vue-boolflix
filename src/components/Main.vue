<template>
  <main class="container-fluid">
    <div class="row">
      <div class="col-12 p-3" id="header">
        <div class="row">
          <div class="col-6">
            <a href="#"><img src="../assets/logo.png" alt="bootflix-font"></a>
          </div>

          <div class="col-6 d-flex justify-content-center align-items-center">
            <input type="text" placeholder="Search">
            <button class="btn-primary">search</button>
          </div>
        </div>
      </div>

      <div class="col-12" id="main-contain">

      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Main',
  props: {
  }
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
