<template>
           
         <nav  class="navbar navbar-expand-lg text-uppercase fixed-top">
            <div class="container">
                <a class="navbar-brand" href="#page-top">Logo ici</a>
                <span class="navbar-toggler display-4 text-dark" @click="show()" type="button" data-bs-toggle="collapse" data-bs-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                   <i v-if="this.click" class="bi bi-list"></i>
                   <i v-else class="bi bi-x-lg"></i>
                </span>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ms-auto text-center">
                        <li class="nav-item mx-0 mx-lg-5"><a class="nav-link py-3 px-0 px-lg-3 "><router-link to="/"><i class="bi bi-house"></i> Home</router-link></a></li>
                        <li class="nav-item mx-0 mx-lg-5"><a class="nav-link py-3 px-0 px-lg-3 "><router-link to="/about"><i class="bi bi-calculator"></i> Claculer Moyenne</router-link></a></li>
                    </ul>
                </div>
            </div>
        </nav>

</template>

<script>
export default {
  name: "App_header",
  data(){
    return {
        click:1
    }
  },
  methods:{
    show(){
         return this.click=this.click ? 0 :1;
    }
  },
  computed:{
    
  }

};
  /*** scrool *///
                window.addEventListener('scroll',function(){
                       const header=document.querySelector('nav');
                       header.classList.toggle('sticky',window.scrollY>0);
                 });
</script>

<style scoped>

li{
    list-style: none;
}

ul li a{
    text-decoration: none;
    font-size:25px;
     color: #ad5623;
    font-weight:600;
}

a:hover{
 transform: scale(1.5);

}

nav {
  padding-top: 1rem;
  padding-bottom: 1rem;
  font-family: "Montserrat", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  font-weight: 700;
}
.sticky{
 background-color:#f5e8d8;
 padding: 10px 70px;
 height: 60px;
}

@media screen and (max-width:991px){
  nav{
    background-color: gray;
  }

}

</style>