<template>
  <div class="black-bg" v-if="modalCheck == true">
    <div class="white-bg">
      <h4>{{ oneroom[clickCount].title }}</h4>
      <img v-bind:src="oneroom[clickCount].image">
      <p>{{oneroom[clickCount].content}}</p>
      <p>가격:{{ oneroom[clickCount].price }}</p>
      
      <!-- <button v-on:click="modalCheck = false">닫기</button> -->
    </div>
  </div>
</template>

<script>


export default {
  name: 'ModalTemplate',
  data(){
    return{
      
    }
  },
  components:{
    
  },
  //props: {데이터이름:자료형이름}
  props:{
    oneroom : Array,
    clickCount: Number,
    modalCheck: Boolean,
  }
  
}
</script>

<style>

</style>