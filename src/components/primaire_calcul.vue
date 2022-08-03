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
          <div style="margin-top: -50px" class="modal-body container">
            <form-wizard @onComplete="Onsubmit">
              {{ moyenne }}
              <div v-for="mod in niveau[select].modules" :key="mod.id">
                <tab-content>
                  <h1 class="text-center fw-bolder mb-3">{{ mod.name }}</h1>
                  <div
                    class="form-control"
                    v-for="mat in mod.matiere"
                    :key="mat.id"
                  >
                    <div class="row gap-2">
                      <input
                        type="number"
                        class="col-md-4 form-control text-center w-50"
                        @keyup="calculate(form[mat].module)"
                        :readonly="mat.indexOf('معدل') !== -1"
                        v-model="form[mat].note"
                      />
                      <label class="col-md-5 text-center">: {{ mat }}</label>
                    </div>
                  </div>
                </tab-content>
              </div>
            </form-wizard>
          </div>
          <div
            v-if="this.field"
            class="modal modal-sheet d-block"
            tabindex="-1"
            role="dialog"
            id="modalSheet"
          >
            <div class="modal-dialog" role="document">
              <div class="modal-content position-static rounded-6 shadow">
                <div class="modal-header border-bottom-0 py-6">
                  <h5 class="modal-title float-end">النتيجة</h5>
                  <button
                    type="button"
                    class="btn-close"
                    data-bs-dismiss="modal"
                    aria-label="Close"
                  ></button>
                </div>
                <div class="modal-body text-center">
                  <p>
                    معدل الثلاثي هو
                    <span :class="moyenne > 10 ? 'text-sucess' : 'text-danger'"
                      >{{ moyenne }}
                    </span>
                  </p>
                </div>
                <div class="modal-footer flex-column border-top-0">
                  <button
                    type="button"
                    @click="initial()"
                    data-bs-dismiss="modal"
                    class="btn btn-lg btn-primary w-100 mx-0 mb-2"
                  >
                    <span :class="moyenne > 10 ? 'text-sucess' : 'text-danger'">
                      {{ moyenne > 10 ? "حسنا" : "للاسف" }}
                    </span>
                  </button>
                </div>
              </div>
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
import { FormWizard, TabContent, ValidationHelper } from "vue-step-wizard";
import niveauCard from "@/components/Card.vue";

import Vue from "vue";
import VueConfetti from "vue-confetti";

Vue.use(VueConfetti);

export default {
  name: "primaire_calcul",
  components: { niveauCard, FormWizard, TabContent },
  mixins: [ValidationHelper],
  data() {
    return {
      select: 0,
      form: {},
      moyenne: 0,
      field: 0,
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
      this.$confetti.start();
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