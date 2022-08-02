<template>
<div class="hello">
    <section class="py-5 ">
            <div class="container px-lg-5 mt-5">
              <div class="hero text-center row">
                <div id="welcome" class="static_text col-lg-12 fw-bolder">Welcome </div>
                    <ul class="dynamique col-lg-6">
                        <li><span>To</span></li>
                        <li><span>Our</span></li>
                        <li><span>New</span></li>
                        <li><span>Website</span></li>
                    </ul>
            </div>
                <div class="row py-5 gap-3">
                       <div class="col-lg-5 py-4">
                            <img src="../assets/Motivation4.jpg" alt="" class="shadow rounded-pill" width="300px" height="300px">
                       </div>
                       <div class="col-md-3 py-5 ">
                           <p style="font-size:22px" class="mt-5 py-5 fw-bolder">
                                 " Success is the most beautiful thing in the world. "
                           </p>
                       </div>
                        <div class="col-lg-2 py-4">
                            <img src="../assets/Best-success-quotes-pics-status-thought-12.jpg" class="shadow rounded-pill" alt="" width="200px" height="300px">
                       </div>
                </div>
            </div>
        </section>           
</div>
  
</template>
   
<script>
export default {
  name: 'HelloWorld',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p,#welcome{
    text-shadow: 5px 5px 5px #403c32;
}
.hero{
    display: flex;
    justify-content: center;
}
.hero .static_text{
    color: #fff;
    font-size: 69px;

}
.hero .dynamique{
    margin-left:15px;
    height: 90px;
    line-height: 90px;
    overflow:hidden;
}

.dynamique li{
    list-style: none;
    color: #16f37d;
    font-size: 68px;
    font-weight: 500;
    position: relative;
    top:0;
    animation: slide 8s steps(4) infinite;
}

@keyframes slide{
    100%{
        top:-360px;
    }
}

.dynamique li span::after{
    content: "";
    position:absolute;
    left: 0;
    height: 100%;
    width: 100%;
    background: 1000;
    border-left: 2px solid #16f37d;
    animation: typing 3s steps(10) infinite;
}

@keyframes typing {
    40%,68%{
        left: calc(100% + 30px);
    }
    100%{
        left: 0;
    }
}
</style>
