<template>
  <div class="cont">
    <niveau-card :titel="titel" :niveau="niveau" @selectNiveau="selectNiveau" />
    <div class="show" v-if="select">
      <h2 class="text-center mb-2">{{ this.niveau[select].name }}</h2>
      <div class="row">
        <div
          v-for="mod in this.niveau[select].modules"
          :key="mod.id"
          class="card col-sm-12 text-center mb-3"
        >
          <div class="card-header text-warning fw-bolder">{{ mod.name }}</div>
          <div v-for="mat in mod.matiere" :key="mat.id" class="card-body">
            <p class="card-text row">
              <input
                class="col-lg-6 text-center"
                type="text"
                v-model="form[mat].note"
                :readonly="mat.indexOf('معدل') !== -1"
                @keyup="calculate(form[mat].module)"
              />
              <label class="col-lg-6 text-center">: {{ mat }}</label>
            </p>
          </div>
        </div>
        <button @click="Onsubmit" class="btn btn-warning">النتيجة</button>
      </div>
    </div>
    <div v-if="congrats == 1">
      <div class="card felicitation" style="width: 18rem">
        <div class="card-body">
          <h5 class="card-title fw-bolder">النتيجة</h5>
          <h6 class="card-subtitle mb-2 text-muted text-center">
            : معدل الثلاثي
          </h6>
          <p class="card-text text-center fw-bolder">
            {{ this.moyenne }}
          </p>
          <button v-on:click="initiale" class="btn btn-warning">
            <span :class="this.moyenne > 10 ? 'text-success' : 'text-danger'">
              {{ this.moyenne > 10 ? "احسنت" : " للاسف" }}
            </span>
          </button>
        </div>
      </div>
    </div>
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
      congrats: 0,
      moyenne: 0,
      field: 1,
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
      this.select = 0;
      this.congrats = 1;
      if (this.moyenne > 10) {
        this.$confetti.start();
      }
    },
    initiale() {
      this.congrats = 0;
      this.$confetti.stop();
    },
  },
  computed: {},
};
</script>

<style scoped>
label {
  font-weight: 600;
}
.show {
  position: absolute;
  top: 120%;
  left: 50%;
  width: 50%;
  z-index: 1;
  background: #fff;
  transform: translate(-50%, -50%);
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.1),
    0 0 0 1000px rgba(255, 255, 255, 0.95);
  padding: 40px;
}
input {
  border: none;
  border-bottom: 1px solid #000;
  outline: none;
}
.felicitation {
  top: 50%;
  position: fixed;
  left: 50%;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.1),
    0 0 0 1000px rgba(255, 255, 255, 0.95);
  transform: translate(-50%, -50%);
}
</style>