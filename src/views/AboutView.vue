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
                    <div class="content">
                           <ol type="7" start="7" >
                                <li ><a href="">Premiere</a> </li>
                                <li><a href="">8</a></li>
                                <li><a href="">neuvième </a></li>
                           </ol>
                    </div>
                </div>
            <div class="face face2">
                <h2>Secondaire</h2>
            </div>
        </div>
    </div>
    </div>
  </div>
</template>
<script>

 export default {
    name:"AboutView"
 }

</script>

<style scoped>

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
