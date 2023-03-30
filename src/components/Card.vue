<template>
  <div>
    <h4>{{ oneroom.title }}</h4>
    <img :src="oneroom.image">
    <p>{{ oneroom.content }}</p>
    <p>가격: {{ oneroom.price }}</p>
  </div>
</template>

<script>
export default {
  name:'CardTemp',
  data(){
    return{
      
    }
  },
  props:{
    oneroom: Object,
    
  }

}
</script>

<style>

</style>