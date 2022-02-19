<template>

  <ModalComponent :popup = "popup" :onerooms = "onerooms" :click = "click"/>

  <div class="menu">
      <a v-for = "baner in baners" :key = "baner">{{ baner }}</a>
  </div>

  <DiscountComponent/>

  <CardComponent :onerooms="onerooms" :popup="popup"/>

</template>

<script>
import data from './assets/oneroom.js';
import DiscountComponent from './components/DiscountComponent.vue';
import ModalComponent from './components/ModalComponent.vue';
import CardComponent from './components/CardComponent.vue';

export default {
  name: 'App',
  data() {
    return {
      baners : ['home', 'menu', 'etc'],
      onerooms : data,
      popup: false,
      click: 0
    }
  },
  components: {
      DiscountComponent: DiscountComponent,
      ModalComponent: ModalComponent,
      CardComponent: CardComponent,
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

.img {
  width: 40%;
}

</style>
