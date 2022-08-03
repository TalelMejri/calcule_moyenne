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
      select: 0
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
   
  },
  computed: {
    
  },
};



</script>

<style scoped>

</style>