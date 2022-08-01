<template>
 
         <nav class="navbar navbar-expand-lg text-uppercase fixed-top" id="mainNav">
            <div class="container">
                <a class="navbar-brand" href="#page-top">Logo ici</a>
                <button class="navbar-toggler text-uppercase font-weight-bold bg-primary text-white rounded" type="button" data-bs-toggle="collapse" data-bs-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                    <i class="fas fa-bars"></i>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item mx-0 mx-lg-5"><a class="nav-link py-3 px-0 px-lg-3 "><router-link to="/">Home</router-link></a></li>
                        <li class="nav-item mx-0 mx-lg-5"><a class="nav-link py-3 px-0 px-lg-3 "><router-link to="/about">About Us</router-link></a></li>
                    </ul>
                </div>
            </div>
        </nav>

</template>

<script>
export default {
  name: "App_header",
};
</script>

<style scoped>

li{
    list-style: none;
}

ul li a{
    text-decoration: none;
    font-size: 20px;
}

nav {
  padding-top: 1rem;
  padding-bottom: 1rem;
  font-family: "Montserrat", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  font-weight: 700;
}
</style>