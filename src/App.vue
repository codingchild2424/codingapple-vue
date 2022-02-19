<template>

  <!-- trainsition 사이에 component를 넣으면, 화면 효과를 넣을 수 있음 -->
  <transition name="fade"> 
    <ModalComponent 
      :popup = "popup" 
      :onerooms = "onerooms" 
      :click = "click" 
      @closeModal="popup = false"
    />
  </transition>

  <div class="menu">
      <a v-for = "baner in baners" :key = "baner">{{ baner }}</a>
  </div>

  <DiscountComponent/>

  <p>지금 결제하면 {{amount}}% 할인</p>

  <button @click="priceSort()">
    가격순 정렬
  </button>

  <button @click="sortBack()">
    되돌리기
  </button>

  <CardComponent 
    :onerooms="onerooms" 
    :popup="popup" 
    @openModal="popup = true; 
    click=$event"
  />

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
      original_onerooms : [...data], //사본을 따로 만드는 문법
      popup: false,
      click: 0,
      amount: 30,
    }
  },
  components: {
      DiscountComponent: DiscountComponent,
      ModalComponent: ModalComponent,
      CardComponent: CardComponent,
  },
  methods : {
    priceSort(){
      this.onerooms.sort(function(a, b){ //그냥 sort를 사용하면, 문자의 순서만 바꿀 수 있음, 따라서 이런 방식으로 사용해야 함
        return a.price - b.price; //onerooms에 있는 가격 정보만 활용해서 순서를 정하므로
      })
    },
    sortBack(){
      this.onerooms = [...this.original_onerooms]; //array는 그냥 등호를 쓰면 값을 공유하게 되므로, [...] 문법을 사용하면 됨
    },
    mounted(){
      setInterval(() => {
        this.amount--;
      }, 1000);
    },
    beforeUpdata(){
      if (this.month == 2){
        alert('2개월은 너무 적음.. 안팝니다.')
      }
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

.img {
  width: 40%;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

</style>
