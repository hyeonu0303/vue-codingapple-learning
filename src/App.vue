<template>
  <!--
    v-if="조건식" / 참일때만 보여줌
    모달창
  -->
  <div class="black-bg" v-if="modal_check == true" >
    <div class="white-bg">
      <h4>{{ oneroom[누른거].title }}</h4>
      <p>{{oneroom[누른거].content}}</p>
      <p>가격:{{ oneroom[누른거].price }}</p>
      <button v-on:click="modal_check = false">닫기</button>
    </div>
  </div>


  <!--
    ● 반복문
    1.반복문은 v-for="작명 in 숫자or데이터" :key="오류났을때 볼 값"
    2.<a v-for="작명 in menu" :key="작명">home</a>
      여기서 데이터에서 반복시킬시 작명은 menu의 데이터가된다.
    3.<a v-for="(a,i) in menu" :key="a">{{ a }}</a>
      왼쪽변수는 array내의 데이터, 오른쪽변수는 1씩증가하는변수

    ● :key="" 의용도
    1.반복문쓸때 꼭 써야함
    2.반복문돌린 요소를 컴퓨터가 구분하기 위해 씀

    ※반복문은 같은태그 여러개일때 쓰면 좋음
    ※데이터 어떻게 만들지 먼저 생각하는게 좋음
  -->
    <div class="menu">
      <!-- <a v-for="작명 in 3" :key="작명">{{ products[작명] }}</a> -->
      <a v-for="작명 in menu" :key="작명">{{ 작명 }}</a>
    </div>

    <div v-for="(a,i) in oneroom" :key="i">
      <h4 @click="modal_check=true; 누른거 = i">{{ oneroom[i].title }}</h4>
      <img :src="a.image">
      <p>{{ a.content }}</p>
      <p>가격: {{ a.price }}</p>
    </div>
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

//상품데이터받아오기
import products from './assets/oneroom.js'

export default {
  name: 'App',
  //data보관함
  data(){
    return{
      누른거: 0,
      menu: ['home','shop','about'],
      price: [50,60,70],
      oneroom: products,
      신고수: [0,0,0],
      modal_check : false,
    }
  },
  
  //함수만드는공간
  methods : {
    increase(){
      this.신고수 += 1;
    }
  },
  components: {

  }
}





</script>
<!--
-동적인 UI만드는법
  0.HTML CSS로 디자인해둔다
  1.UI의 현재 상태를 데이터로 저장해둔다
  2.데이터가변하면 HTML이 어떻게 보일지 작성
-->
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
/*모달창S */
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
/*모달창E */
</style>
