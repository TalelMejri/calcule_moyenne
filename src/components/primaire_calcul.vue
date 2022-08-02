<template>
  <div class="cont">
    <div class="container py-5">
      <div class="row py-5">
        <div class="card mt-5">
          <div class="face face1">
            <div class="content">
              <ol type="1" class="mt-5 py-2">
                <li
                  @click="update(index)"
                  v-for="(prim, index) in primaire"
                  :key="prim.id"
                >
                  <a
                    data-bs-toggle="modal"
                    data-bs-target="#exampleModal"
                    href="#"
                    >{{ primaire[index] }}</a
                  >
                </li>
              </ol>
            </div>
          </div>
          <div class="face face2">
            <h2>{{ titel }}</h2>
          </div>
        </div>
      </div>
    </div>

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
            <form class="shadow rounded pt-5" onsubmit.prevent="OnSubmit">
              <div class="row pt-5">

              <div class="matier1 card col-lg-3 pt-5">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                 <span @click="matiere1=1" class="btn btn-primary">suivant</span>
              </div>

               <div v-if="matiere1" class="matier2 card col-lg-3 py-5">
                 <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                 <span  @click="matiere2=1" class="btn btn-primary">suivant</span>
              </div>

               <div v-if="matiere2" class="matier3 card col-lg-3 py-5">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                  <input type="text" required class="form-control mb-3">
                 <button  @click="resultat=1" class="btn btn-primary">suivant</button>
              </div>

              <div v-if="resultat" class="resultat card col-lg-3">
                  this is resulatat
                 <button @click="matiere1=0,matiere2=0,resultat=0"  
                 data-bs-dismiss="modal"
                 type="submit" class="btn btn-primary">Confirme</button>
              </div>
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
export default {
  name: "primaire_calcul",
  data() {
    return {
      select: 0,
      matiere1:0,
      matiere2:0,
      matiere3:0,
      resultat:0
    };
  },
  props: {
    primaire: Array,
    titel: String,
  },
  methods: {
    update(index) {
      this.select = index;
    },
  },
  computed: {},
};
</script>

<style scoped>
.container .card {
  position: relative;
  width: 300px;
  height: 400px;
  margin: 0 auto;
  background: #fff;
  transition: 0.5s;
}
.container .card:hover {
  box-shadow: 0 30px 50px rgba(0, 0, 0, 0.2);
}
.container .card .face {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.container .card .face.face1 {
  box-sizing: border-box;
  padding: 20px;
  text-align: center;
  background: #fff;
  color: #013d4a;
}
.container .card .face.face1 h2 {
  margin-top: 70px;
}
.container .card .face.face2 {
  background: url(../assets/Capture.PNG);
  transition: 0.5s;
}
.container .card:hover .face.face2 {
  height: 80px;
  width: 80px;
  cursor: pointer;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  background: transparent;
}

.container .card .face.face2 h2 {
  margin: 0;
  padding: 0;
  font-size: 25px;
  font-weight: 600;
  color: #000;
  transition: 0.5s;
}

.container .card:hover .face.face2 h2 {
  color: #013d4a;
  font-size: 2em;
}

li {
  text-align: center;
  line-height: 40px;
}
a {
  text-decoration: none;
  font-size: 25px;
}

a:hover {
  color: red;
  border-bottom: 1px solid #000;
}
</style>