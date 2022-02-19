<template>

  <div v-if = "popup == true" class="black-bg">
   <div class="white-bg">
     <h4>{{onerooms[click].title}}</h4>
     <img :src="onerooms[click].image" class = "img">
     <button @click="popup = false">닫기</button>
   </div>
  </div>

  <div class="menu">
    <a v-for = "baner in baners" :key = "baner">{{ baner }}</a>
  </div>
  <div>
    <div v-for = "(oneroom, i) in onerooms" :key="(oneroom, i)">
      <h1 @click = "popup = true; click = i">{{oneroom.title}}</h1>
      <img :src="oneroom.image" class = "img">
      <h4>{{oneroom.content}}</h4>
      <h4>{{oneroom.price}}원</h4>
    </div>
  </div>
</template>

<script>
import data from './assets/oneroom.js'

export default {
  name: 'App',
  data() {
    return {
      baners : ['home', 'menu', 'etc'],
      onerooms : data,
      popup: false,
      click: 0
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}

.menu a {
  color : white;
  padding : 10px;
}

.black-bg {
  width: 80%; height: 60%;
  background: rgba(0,0,0,0,5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 80%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.img {
  width: 40%;
}

</style>
