<template>
  <div class="cont">
    <niveau-card :niveaux="primaire" :titel="titel" @selectNiveau="selectNiveau"/>
    <div
      class="modal fade"
      id="exampleModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-fullscreen">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="d-flex justify-content-center">
              {{ primaire[this.select] }}
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body container">
            <form class="shadow rounded pt-5">
              <div class="row pt-5">

             </div>
            </form>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Close
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>  

import niveauCard from '@/components/Card.vue';
export default {
  name: "primaire_calcul",
  components:{niveauCard},
  data() {
    return {
      select: 0,
      matiere1:0,
      matiere2:0,
      matiere3:0,
      resultat:0,
      mat1:0,
      mat2:0
    };
  },
  props: {
    primaire: Array,
    titel: String,
  },
  methods: {
    selectNiveau(index) {
      this.select = index;
    },
    update1(){
        let m=document.getElementsByName('mat1');
        let count=0;
        m.forEach(v=>{
            count+=parseInt(v.value);
        });
         this.mat1=count/4;
         this.matiere1=1;
      },
    update2(){
        let m=document.getElementsByName('mat2');
        let count=0;
        m.forEach(v=>{
            count+=parseInt(v.value);
        });
         this.mat2=count/4;
         this.matiere2=1;
      },
       update3(){
        let m=document.getElementsByName('mat3');
        let count=0;
        m.forEach(v=>{
            count+=parseInt(v.value);
        });
         this.mat3=count/4;
         this.resultat=1;
      },
     
  },
  computed: {
    
  },
};



</script>

<style scoped>
@import url("@/assets/css/style.css");
</style>