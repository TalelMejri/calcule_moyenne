<template>
  <div class="home py-5">

        <HelloWorld></HelloWorld>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
}
}
</script>

<style scoped>
   
   .home{
        background-image: url(../assets/Capture.PNG);
        background-repeat: no-repeat;
        background-size: cover;
        background-attachment: fixed;
        background-position: top ;
        height:100%;
        width: 100wh;
    }
@media screen and (max-width:450px){

    

}
</style>
