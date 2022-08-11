<template>
  <div class="college">
    <card
      v-if="show_card"
      :titel="titel"
      :niveau="niveau"
      @selectNiveau="selectNiveau"
    ></card>
    <div class="show" v-if="select">
      <h2 class="text-center mb-2">{{ this.niveau[select].name }}</h2>
      <div class="row">
        <div
          v-for="mod in this.niveau[select].modules"
          :key="mod.id"
          class="card col-sm-12 text-center mb-3"
        >
          <div class="card-header text-warning fw-bolder">
            {{ mod.name }}
            {{ moyenne }}
          </div>
          <div v-for="mat in mod.matiere" :key="mat.id" class="card-body">
            <p class="card-text row">
              <input
                class="col-lg-6 text-center"
                @keyup="calculate(form[mat.name].module)"
                v-model="form[mat.name].note"
                type="text"
              />
              <label class="col-lg-6 text-center">: {{ mat.name }}</label>
            </p>
          </div>
        </div>
        <button class="btn btn-warning">النتيجة</button>
      </div>
    </div>
  </div>
</template>

<script>
import card from "@/components/Card.vue";
export default {
  name: "college_calcul",
  props: {
    niveau: Object,
    titel: String,
    show_card: Boolean,
  },
  components: {
    card,
  },
  data() {
    return {
      select: 0,
      form: {},
      moyenne: 0,
    };
  },
  methods: {
    selectNiveau(index) {
      this.select = index;
      this.$emit("selection");
    },
    calculate(module) {
      let sum = 0;
      let count = 0;
      let lastnote = 0;
      let key = "";
      Object.values(this.form).forEach((v) => {
        if (v.module == module) {
          sum += parseInt(v.note) * v.coef || 0;
          lastnote = parseInt(v.note) * v.coef || 0;
          count += v.coef ? v.coef : 0;
          key = v.name;
        }
      });
      this.form[key].note = ((sum - lastnote) / count).toFixed(2);
      count = 0;
      sum = 0;
      Object.values(this.form).forEach((val) => {
        if (val.name.indexOf("معدل") !== -1) {
          sum += parseInt(val.note) * val.coef_domaine || 0;
          count += val.coef_domaine;
        }
      });
      this.moyenne = (sum / count).toFixed(2);
    },
  },
  watch: {
    select() {
      let form = {};
      for (let mod in this.niveau[this.select].modules) {
        for (let mat in this.niveau[this.select].modules[mod].matiere) {
          let m = new Object({
            name: this.niveau[this.select].modules[mod].matiere[mat].name,
            coef: this.niveau[this.select].modules[mod].matiere[mat].coef,
            note: 0,
            module: mod,
            coef_domaine: this.niveau[this.select].modules[mod].coef,
          });
          form[m.name] = m;
        }
      }
      this.form = form;
    },
  },
};
</script>

<style>
</style>