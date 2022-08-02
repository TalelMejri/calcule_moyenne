<template>
  <div id="app">
    <App_Header></App_Header>
    <router-view/>
    <App_footer></App_footer>
     <div class="loader-container">
        <img src="./assets/logo.png" alt="Loading">
    </div>
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

 /*** loading *///
    function loader(){
        document.querySelector('.loader-container').classList.add('fade-out');
    }
    function fadeOut(){
        setInterval(loader,2000);
    }
    window.onload = fadeOut();

</script>
<style scoped>
.loader-container{
    position: fixed;
    top:0; left:0;
    z-index: 10000;
    background-color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    height:100%;
    width:100%;
  }
  .loader-container.fade-out{
    top:-120%;
  }
  .loader-container img{
    padding:1rem;
  }

</style>
