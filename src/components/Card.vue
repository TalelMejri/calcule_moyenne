<template>
  <div class="container py-5">
    <div class="row py-5">
      <div class="card mt-5">
        <div class="face face1">
          <div class="content py-5">
            <ol type="1" class="mt-5 py-5">
              <li
                class="mt-2"
                @click="$emit('selectNiveau', index)"
                v-for="(prim, index) in niveau"
                :key="prim.id"
              >
                <a
                  data-bs-toggle="modal"
                  data-bs-target="#exampleModal"
                  href="#"
                  >{{ prim.name }}</a
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
  props: {
    titel: String,
    niveau: Object,
  },
};
</script>

<style scoped>
@import url("@/assets/css/style.css");
</style>