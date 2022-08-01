<template>
  <div class="about py-5">
    <div class="container py-5">
    <div class="row py-5">
            <div class="card mt-5">
                <div class="face face1">
                    <div class="content">
                           <ol type="1" class="mt-5 py-2">
                                <li ><a href="">Premire</a> </li>
                                <li><a href="">deuxieme</a></li>
                                <li><a href="">troisime</a></li>
                                <li><a href="">qutrieme</a></li>
                                <li><a href="">cinquieme</a></li>
                                <li><a href="">sixieme</a></li>
                           </ol>
                    </div>
                </div>
                <div class="face face2">
                    <h2>Primaire</h2>
                </div>
            </div>

            <div class="card mt-5">
                <div class="face face1">
                    <div class="content">
                           <ol type="7" start="7" class="mt-5 py-2">
                                <li ><a href="">septieme</a> </li>
                                <li><a href="">8</a></li>
                                <li><a href="">neuvième </a></li>
                           </ol>
                    </div>
                </div>
                <div class="face face2">
                    <h2>Préparatoire</h2>
                </div>
            </div>

        <div class="card mt-5">
           <div class="face face1">
                 <i v-if="opacity || clair || bac" @click="initial" id="close" class="bi bi-x-lg"></i>
                    <div class="content">
                        <div class="modale mt-4 py-4" v-if="opacity==1 || clair==1 || bac==1">
                            <ol type="1" class="mt-5 py-2">
                                <li ><a href="">info</a> </li>
                                <li><a href="">technique</a></li>
                                <li><a href="">math</a></li>
                                <li><a href="">science</a></li>
                                <li><a href="">eco</a></li>
                                <li><a href="">lettre</a></li>
                                <li><a href="">sport</a></li>
                           </ol>
                        </div>
                           <ol v-else type="7" start="7" >
                                <li ><a href="">Premiere</a> </li>
                                <li><a href="#"  @click="show">2éme </a></li>
                                <li><a href="#" @click="clean">3eme </a></li>
                                <li><a href="#" @click="show_bac">Bac </a></li>
                           </ol>
                    </div>
                </div>
            <div class="face face2">
                <h2 v-if="opacity==0 && clair==0 && bac==0"> Secondaire</h2>
                <h2 v-else-if="opacity==1"> 2éme</h2>
                <h2 v-else-if="clair==1"> 3éme</h2>
                <h2 v-else-if="bac==1">Bac</h2>
            </div>
        </div>

    </div>
    </div>
  </div>
</template>
<script>

 export default {
    name:"AboutView",
    data(){
        return{
            opacity:0,
            clair:0,
            bac:0
        }
    },
    methods: {
        show(){
            return this.opacity=1;
        },
        clean(){
            return this.clair=1;
        },
        show_bac(){
            return this.bac=1;
        },
        initial(){
            this.bac=0;
            this.clair=0;
            this.opacity=0;
        }
    },
 }
 

</script>

<style scoped>
#close{
    margin-top:-350px;
    margin-left: -240px;
    position: absolute;
    cursor: pointer;
}
#close:hover{
    transform: scale(1.5);
    color:red;
}
.container .card{
    position: relative;
    width: 300px;
    height: 400px;
    margin: 0 auto;
    background: #fff;
    transition: 0.5s;
}
.container .card:hover{
    box-shadow: 0 30px 50px rgba(0,0,0,.2);
}
.container .card .face{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.container .card .face.face1{
   box-sizing: border-box;
   padding: 20px;
   text-align: center;
   background: #fff;
   color: #013d4a;
}
.container .card .face.face1 h2{
    margin-top: 70px;
}
.container .card .face.face2{
    background:url(../assets/Capture.PNG);
    transition: 0.5s;
}
.container .card:hover .face.face2{
    height: 80px;
    width: 80px;
    cursor: pointer;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    background: transparent;
}

.container .card .face.face2 h2{
    margin: 0;
    padding: 0;
    font-size:25px;
    font-weight: 600;
    color:#000;
    transition: 0.5s;
}

.container .card:hover .face.face2 h2{
    color: #013d4a;
    font-size: 2em;
}

li{

    text-align: center;
    line-height: 40px;
}
a{
    text-decoration: none;
    font-size: 25px;
}





</style>
