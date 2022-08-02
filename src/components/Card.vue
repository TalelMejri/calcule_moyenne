<template>
  <div class="container py-5">
      <div class="row py-5">
        <div class="card mt-5">
          <div class="face face1">
            <div class="content">
              <ol type="1" class="mt-5 py-2">
                <li
                  @click="$emit('selectNiveau',index)"
                  v-for="(prim, index) in niveaux"
                  :key="prim.id"
                >
                  <a
                    data-bs-toggle="modal"
                    data-bs-target="#exampleModal"
                    href="#"
                    >{{ niveaux[index] }}</a
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
</template>

<script>
export default {
    props:{
      niveaux: Array,
      titel: String,
    }
}
</script>

<style>

</style>