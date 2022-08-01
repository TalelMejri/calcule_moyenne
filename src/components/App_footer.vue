<template> 
    <div class="foot">
        <div class="row bg-dark py-5">
            <div class="col-lg-12 text-center">
                <div class="row">
                     <h4 class="text-white text-center mb-4">Our Amazing Team</h4>
                    <div class="col-lg-6  text-center mb-2">
                        <img src="../assets/chlendi.jpg" alt="Youssef Chlendi" width="150px" height="150px" class="mx-auto rounded-circle">
                        <p class="text-white mt-1">Youssef Chlendi</p>
                            <a class="mx-2"  href="#" ><i class="bi bi-facebook"></i></a>
                            <a class="mx-2"  href="#"><i class="bi bi-instagram"></i></a>
                            <a class="mx-2" href="#" ><i class="bi bi-github"></i></a>
                          
                    </div>
                     <div class="col-lg-6 text-center">
                        <img src="../assets/talel.jpg" alt="Talel Mejri" width="150px" height="150px" class="mx-auto rounded-circle">
                        <p class="text-white mx-3 mt-1">Talel Mejri</p>
                            <a class="mx-2"  href="#" ><i class="bi bi-facebook"></i></a>
                            <a class="mx-2"  href="#"><i class="bi bi-instagram"></i></a>
                            <a class="mx-2"  href="#" ><i class="bi bi-github"></i></a>
                    </div>
                </div>
            </div>
                </div>
                <div class="row bg-secondary ">
            <p class="text-center text-white mt-3">Copyright 2022-2023 &copy; </p>
            <p class="text-center lead"> {{date}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name:'App_footer',
    data(){
        return{
            date:new Date(),
        }
    }
}
</script>

<style scoped>
    li{
        color: #fff
    };
</style>