<template>
  <div class="cont">
    <niveau-card :titel="titel" :niveau="niveau" @selectNiveau="selectNiveau" />
    <div
      v-if="select"
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
              {{ niveau[select].name }}
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body container">
          {{moyenne}}
            <div v-for="mod in niveau[select].modules" :key="mod.id">
              <h1>{{ mod.name }}</h1>
              <span v-for="mat in mod.matiere" :key="mat.id"
                >{{ mat }}
                <input
                  type="number"
                  @keyup="calculate(form[mat].module)"
                  :readonly="mat.indexOf('معدل') !== -1"
                  v-model="form[mat].note" />

                <br
              /></span>
              <br />
            </div>
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
import niveauCard from "@/components/Card.vue";
export default {
  name: "primaire_calcul",
  components: { niveauCard },
  data() {
    return {
      select: 0,
      form: {},
      moyenne: 0,
    };
  },
  watch: {
    select() {
      let form = {};
      for (let mod in this.niveau[this.select].modules) {
        for (const mat in this.niveau[this.select].modules[mod].matiere) {
          let m = new Object({
            name: this.niveau[this.select].modules[mod].matiere[mat],
            note: 0,
            module: mod,
          });
          form[m.name] = m;
        }
      }
      this.form = form;
    },
  },
  props: {
    // primaire: Array,
    titel: String,
    niveau: Object,
  },
  methods: {
    selectNiveau(index) {
      this.select = index;
    },
    calculate(module) {
      let count = 0;
      let sum = 0;
      let lastNote = 0;
      let key = "";
      Object.values(this.form).forEach((val) => {
        if (val.module == module) {
          sum += parseInt(val.note) || 0;
          lastNote = parseInt(val.note) || 0;
          count++;
          key = val.name;
        }
      });
      this.form[key].note = (sum - lastNote) / (count - 1);
      count=0;
      sum=0;
      Object.values(this.form).forEach((val) => {
        if (val.name.indexOf('معدل') !== -1){
            count++;
            sum+=val.note;
        }
      });
      this.moyenne=sum/count;
    },
  },
  computed: {},
};
</script>

<style scoped>
</style>