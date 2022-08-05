<template>
  <div class="cont">
    <niveau-card :titel="titel" :niveau="niveau" @selectNiveau="selectNiveau" />
  </div>
</template>

<script>
import { FormWizard, TabContent, ValidationHelper } from "vue-step-wizard";
//import { required, between } from "vuelidate/lib/validators";
import niveauCard from "@/components/Card.vue";
import Vue from "vue";
import VueConfetti from "vue-confetti";

Vue.use(VueConfetti);

export default {
  name: "primaire_calcul",
  components: { niveauCard, FormWizard, TabContent, ValidationHelper },
  mixins: [ValidationHelper],
  data() {
    return {
      select: 0,
      form: {},
      moyenne: 0,
      field: 0,
      /*validationRules: {
      form: {
          required,
          numeric,
          between: between(0, 20),
        },
      },*/
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
      count = 0;
      sum = 0;
      Object.values(this.form).forEach((val) => {
        if (val.name.indexOf("معدل") !== -1) {
          count++;
          sum += val.note;
        }
      });
      this.moyenne = sum / count;
    },
    Onsubmit() {
      this.field = 1;
      this.$confetti.Onsubmit();
    },
    initial() {
      this.field = 0;
    },
  },
  computed: {},
};
</script>

<style scoped>
label {
  font-weight: 600;
}
</style>