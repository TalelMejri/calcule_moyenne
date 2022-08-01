<template>
  <div class="container-fluid ">
     <nav class="navbar navbar-expand-lg shadow">
        <a class="navbar-brand mx-5 position-absolute" href="#">Logo ici</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse d-flex justify-content-center" id="navbarSupportedContent">
          <ul class="nnav navbar-nav ">
            <li class="nav-item ">
              <a class="nav-link active mx-4 display-5" aria-current="page" href="#"> <router-link to="/">Home</router-link></a>
            </li>
            <li class="nav-item">
              <a class="nav-link mx-5 display-2" href="# "> <router-link to="/about">About Us</router-link></a>
            </li>
          </ul>
        </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "App_header",
};
</script>

<style scoped>
</style>