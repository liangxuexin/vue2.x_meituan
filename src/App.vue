<template>
  <div id="app">
    <!--header-->
    <app-header :poiInfo="poiInfo"></app-header>
    <!--nav-->
    <app-nav></app-nav>
    <!--content-->
    <router-view></router-view>
  </div>
</template>

<script>
import Header from "./components/header/Header";
import Nav from "./components/nav/Nav";
export default {
  name: 'App',
  components:{
    'app-header':Header,
    'app-nav':Nav
  },
  created(){
    // axios

    //fetch
    fetch('api/goods')
    .then(response => {
      return response.json();
    })
    .then(response => {
      // console.log(response)
      if( response.code == 0 ){
        this.poiInfo = response.data.poi_info;
      }
    })
  },
  data(){
    return{
      poiInfo :{}
    }
  }
}
</script>

<style>

</style>
