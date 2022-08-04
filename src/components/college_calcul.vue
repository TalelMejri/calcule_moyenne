<template>
  <div class="college">
    <card :titel="titel" :niveau="niveau" @selectNiveau="selectNiveau"></card>
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
              <div v-for="mod in niveau[select].modules" :key="mod.id">
                <tab-content>
                  <h1 class="text-center fw-bolder mb-3">
                    {{ mod.name }}
                  </h1>
                  <div
                    v-for="mat in mod.matiere"
                    :key="mat.id"
                    class="form-control"
                  >
                    <div class="row gap-2">
                      <input
                        id="form"
                        type="number"
                        :readonly="mat.indexOf('معدل') !== -1"
                        class="col-md-4 form-control text-center w-50"
                        v-model="form[mat].note"
                      />

                      <label class="col-md-5 text-center">{{ mat }}</label>
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
          ></div>
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
import card from "@/components/Card.vue";
export default {
  name: "college_calcul",
  props: {
    niveau: Object,
    titel: String,
  },
  components: {
    card,
    FormWizard,
    TabContent,
  },
  data() {
    return {
      select: 0,
      form: {},
    };
  },
  methods: {
    selectNiveau(index) {
      this.select = index;
    },
  },
  watch: {
    select() {
      let form = {};
      for (let mod in this.niveau[this.select].modules) {
        for (let mat in this.niveau[this.select].modules[mod].matiere) {
          let m = new Object({
            name: this.niveau[this.select].modules[mod].matiere[mat],
            note: 0,
            coef: this.niveau[this.select].modules[mod].coef,
            module: mod,
          });
          form[m.name] = m;
        }
        this.form = form;
      }
    },
  },
};
</script>

<style>
</style>