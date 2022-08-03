<template>
  <div id="app">
    <App_Header></App_Header>
    <router-view/>
    <App_footer></App_footer>
  </div>
</template>

<script>
import App_Header from "./components/App_Header.vue";
import App_footer from "./components/App_footer.vue";

 export default {
    name:'app',
    components:{
       App_Header,App_footer
    }
 }

</script>
<style scoped>


</style>
