<template>
  <div id="app">
    <!-- <vue-simple-spinner class="display-2 mt-5 py-5" size="large" />-->
    <App_Header></App_Header>
    <router-view/>
    <App_footer></App_footer>
  </div>
</template>

<script>
import App_Header from "./components/App_Header.vue";
import App_footer from "./components/App_footer.vue";
//import VueSimpleSpinner from 'vue-simple-spinner';
 export default {
    name:'app',
    components:{
       App_Header,App_footer
       //,VueSimpleSpinner
    }
 }

</script>
<style scoped>


</style>
