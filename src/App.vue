<template>
  <Modal @closeModal="checkModal=false" :products="products" :clickNum="clickNum" :checkModal="checkModal" />

  <div class="menu">
    <a v-for="a in menus" :key="a">{{a}}</a>
  </div>

  <button @click="priceSort">가격 오름차순 정렬</button>
  <button @click="reverseSort">가격 내림차순 정렬</button>
  
  
  <Card @openModal="checkModal=true; clickNum=$event" :product="products[i]" v-for="(a,i) in products" :key="i"/>
  
  
</template>

<script>
import products from './assets/products.js';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  data(){
    return{
      productsOrigin : [...products],
      clickNum : 0,
    checkModal : false,
    price : ['70', '60', '50'],  
    menus : ['Home', 'Products', 'About'],
    products : [...products],
    }
  },
  methods: {
      reverseSort(){
        this.products.sort(function(a,b){
          return b.price - a.price
        })
      },
      sortBack(){
        this.products = [...this.productsOrigin]
      },
      priceSort(){
        this.products.sort(function(a,b){
          return a.price - b.price
        })
      }
    },
    mounted() {
      
    },
  components: {
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>

body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
.room-img{
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
</style>
