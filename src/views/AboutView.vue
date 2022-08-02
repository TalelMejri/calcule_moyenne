<template>
  <div class="about py-5">
    <primaire_calcul :primaire="primaire" :titel="titel"></primaire_calcul>
  </div>
</template>
<script>
import primaire_calcul from '@/components/primaire_calcul.vue'

 export default {
 name:"AboutView",
 data(){
    return{   
        titel:'primaire',
        primaire:['Premire','deuxieme','troisime','qautrieme','cinquieme','sixieme'],
    }
 },
  components: {
     primaire_calcul
  },
 
 }
 
</script>

<style scoped >



</style>
