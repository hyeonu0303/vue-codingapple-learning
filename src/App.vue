<template>
  <!--모달창--> <!--작명="데이터이름" 데이터이름과 똑같이 쓰는게좋음-->
  <!--부모도 쓰는데이터라면 부모컴포넌트에 만들어두기-->
  <ModalTemplate 
    :oneroom="oneroom" 
    :clickCount="clickCount"
    :modalCheck="modalCheck"
    />
  
  <!--메뉴바-->
  <div class="menu">
    <a v-for="i in menu" :key="i">{{ i }}</a>
  </div>

  <!--할인배너(컴포넌트사용)
  많이사용할것만 하는게 좋음 
  -->
  <Discount/>

  <!--템플릿-->
  <Card :oneroom="oneroom[i]" v-for="(작명,i) in oneroom" :key="작명"/>
  <!-- <Card :oneroom="oneroom[1]"/>
  <Card :oneroom="oneroom[2]"/>
  <Card :oneroom="oneroom[3]"/>
  <Card :oneroom="oneroom[4]"/>
  <Card :oneroom="oneroom[5]"/> -->

</template>

<script>
/*
방법1
  import apple from './assets/oneroom.js';
  apple;
  console.log(apple); 
*/

/* 
방법2
  import {apple, apple2} from './assets/oneroom.js';
  apple;
  apple2; 
*/

import products from './assets/oneroom.js';
import Discount from './components/Discount.vue';
import ModalTemplate from './components/ModalTemplate.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  data(){
    return{
      object : {name:'kim', age:20},
      clickCount: 0,
      menu: ['home','shop','about'],
      price: [50,60,70],
      oneroom: products,
      modalCheck : false, 
    }
  },
  
  methods : {
    
  },
  components: {
    Discount: Discount,
    ModalTemplate: ModalTemplate,
    Card : Card,
  }
}
/*
반응형 웹 만드는법
data추가하고 HTML을 조작한다.
*/




</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color:white;
  padding:10px;
}
.room-img{
  width: 70%;
  margin-top: 40px;
}
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
.discount{
  background: #eee;
  padding: 10px;
  margin:10px;
  border-radius: 5px;
}
</style>
