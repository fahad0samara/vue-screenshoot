<script setup>
import { ref } from "vue";
// import { RouterLink, RouterView } from "vue-router";
import axios from "axios"

const url=ref('')
const screenshot=ref('')
const submit = async() => {
 try {
const res=await fetch('http://localhost:2020/screen', {
  method:'post',  
  headers: {'Content-Type': 'application/json'},
  body:JSON.stringify({
    url: url.value
  })  

}).then(data => data.json())
console.log(res);
screenshot.value=`http://localhost:2020/static/screen/${res.id}.png`
 } catch (error) {
   console.log(error);
   
 }
}
</script>

<template>

 <div/>
 

 <div class="container-fluid">
<!-- Background animation-->
    <div class="background">
       <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
      <div class="cube"></div>
         <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
      <div class="cube"></div>
           <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
      <div class="cube"></div>
         <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
       <div class="cube"></div>
      <div class="cube"></div>
    </div>
<!-- header -->
   <header>
<!-- navbar -->
  
<!-- logo -->
      <div class="logo"><span></span></div>
<!-- title & content -->
      <section class="header-content ">
         <h1 class=" font-extrabold">Welcome</h1>
        <p class=" font-black"> Welcome to our screenshot. <br>Put the link here to take a screenshot,
         </p>
       
     	<form @submit.prevent="submit">
    	<input v-model="url" class=" p-4 border-b mr-0  text-3xl  text-white   bg-transparent" placeholder="put the link here"/>
	
<br>
   <button>Take it</button>
       </form>
       <a v-if="screenshot !=''" :href="screenshot" download>
       <img :src="screenshot" alt="">
       
       </a>
      </section>
  </header>

 </div>
  

</template>
<style scoped>

.container-fluid{
  height: 100%;
  margin: 0;
  padding: 0;
  width: 100%;
  background: #FFF;
}
/* ============= Animation background ========= */
.background {
  background: linear-gradient(40deg, #f80303,#080808 ,#080808);
  background-size: 400% 400%;
  animation: Gradient 15s ease infinite;
  position: relative;
  height: 100vh;
  width: 100%;
  overflow: hidden;
  padding:0;
  margin:0px;
}
.cube {
  position: absolute;
  top: 80vh;
  left: 45vw;
  width: 10px;
  height: 10px;
  border: solid 1px #0c0c0c;
  transform-origin: top left;
  transform: scale(0) rotate(0deg) translate(-50%, -50%);
  animation: cube 12s ease-in forwards infinite;
}
.cube:nth-child(2n) {
  border-color: rgb(227, 243, 10) ;
}

.cube:nth-child(2) {
  animation-delay: 2s;
  left: 25vw;
  top: 40vh;
}

.cube:nth-child(3) {
  animation-delay: 4s;
  left: 75vw;
  top: 50vh;
}
.cube:nth-child(4) {
  animation-delay: 6s;
  left: 90vw;
  top: 10vh;
}
.cube:nth-child(5) {
  animation-delay: 8s;
  left: 10vw;
  top: 85vh;
}

.cube:nth-child(7) {
  animation-delay: 10s;
  left: 50vw;
  top: 10vh;
}

/* ================= Header ============ */
header{
  position: absolute;
  top:0%;
  left: 0%;
  width:100%;
  margin: 0;
  padding: 0;
}

.header-content{
  margin-top:5%;
  text-align: center;
  color:  #EFEEF5;
}
.header-content h1{
  text-transform: uppercase;
  font-size: 3em;
  letter-spacing: 1px;
}
.header-content p {
  font-size: 20px;
  line-height: 1.5;
  margin: 20px auto;
}
.header-content button{
  width: 140px;
  margin:30px 10px;
  color: #591BC5;
  font-size: 17px;
  border:1px solid #EFEEF5;
  font-weight: 500;
  background: #EFEEF5;
  border-radius: 20px;
  padding: 10px;
  cursor:pointer;
  transition: .3s;
}
.header-content button:hover{
  border-radius: 0;
}
/* Animate Background*/
@keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
@keyframes cube {
  from {
    transform: scale(0) rotate(0deg) translate(-50%, -50%);
    opacity: 0;
  }
  to {
    transform: scale(20) rotate(960deg) translate(-50%, -50%);
    opacity: 1;
  }
}

</style>

