<template>
  <!--
    v-if="조건식" / 참일때만 보여줌
    모달창
  -->
  <div class="black-bg" v-if="모달창열렸니 == true" >
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지내용</p>
      <button v-on:click="모달창열렸니 = false">닫기</button>
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

    <div v-for="(oneroom,i) in products" :key="i">
      <img src="./assets/room0.jpg" class="room-img">
      <h4 v-on:click="모달창열렸니 = true">{{ oneroom }}</h4>
      <p>{{price[i]}}만원</p>
      <button v-on:click="신고수[i]++">허위매물신고</button>
      <span>신고수: {{ 신고수[i] }}</span>
    </div>
    
    
  
</template>

<script>

/*
암기
{{데이터바인딩}} 하는 이유
1.html 하드코딩하면 변경 힘들어서 하는거임(매일 변경되거나 그러기때문)
2.vue의 실시간 자동 렌더링 쓰려고
자주 변할거같은데이터들은 데이터로 보관하고 HTML에 꽂아넣기{{}}
안바뀔거같은건 하드코딩 ㄱㄱ
*/
export default {
  name: 'App',
  //data보관함
  data(){
    return{
      menu: ['home','shop','about'],
      price: [50,60,70],
      products :['역삼동원룸', '천호동원룸', '마포구원룸'],
      신고수: [0,0,0],
      모달창열렸니 : false,
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
  2.데이터에따라 UI가 어떻게 보일지 작성
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
