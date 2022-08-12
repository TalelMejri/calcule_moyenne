<template>
  <div class="card felicitation" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title fw-bolder">النتيجة</h5>
      <h6 class="card-subtitle mb-2 text-muted text-center">: معدل الثلاثي</h6>
      <p class="card-text text-center fw-bolder">
        {{ moyenne }}
      </p>
      <button @click="ok" class="btn btn-warning">
        <span :class="moyenne > 10 ? 'text-success' : 'text-danger'">
          {{ moyenne > 10 ? "احسنت" : " للاسف" }}
        </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "resultat",
  props: {
    moyenne: Number,
    congrats: Boolean,
  },
  methods: {
    ok() {
      this.$emit("done");
    },
  },
};
</script>

<style scoped>
.felicitation {
  top: 50%;
  position: fixed;
  left: 50%;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.1),
    0 0 0 1000px rgba(255, 255, 255, 0.95);
  transform: translate(-50%, -50%);
}
</style>