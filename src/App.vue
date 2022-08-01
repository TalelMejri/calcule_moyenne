<template>
  <div id="app">
    <App_Header></App_Header>
    <router-view/>
  </div>
</template>

<script>
import App_Header from "./components/App_Header.vue";
 export default {
    name:'app',
    components:{
       App_Header
    }
 }
</script>
<style>
 

</style>
