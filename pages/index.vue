<template>
  <div>
    oii
    
    <Cartao />
  </div>
</template>

<script>


import Cartao from '../components/Cartao.vue';
export default {
  name: "mainPage",
  components:{
    Cartao
  },
  data(){
    return {
      noticias: []
    }
  },
  mounted(){
    //firebase query noticias
  }
}
</script>

<style>

</style>