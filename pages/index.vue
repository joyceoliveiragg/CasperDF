<template>
  <div>
    
    <Cartao v-for="noticia in noticias" :key="noticia.titulo" :noticia="noticia"/>
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
      noticias:  [//{titulo: "teste", descricao: "ola", imagem: "https://www.petz.com.br/blog/wp-content/uploads/2019/04/quantos-anos-vive-um-gatinho.jpg "}, 
     // { titulo: "teste", descricao: "ola", imagem: "https://www.petz.com.br/blog/wp-content/uploads/2019/04/quantos-anos-vive-um-gatinho.jpg "}, 
 // {titulo: "teste", descricao: "ola", imagem: "https://www.petz.com.br/blog/wp-content/uploads/2019/04/quantos-anos-vive-um-gatinho.jpg "}
 ]
    }
  },
  async mounted(){
    //firebase query noticias
    var collection = await this.$fire.firestore.collection('noticias').get()
    collection.forEach(doc => {
      let noticia = doc.data()
      this.$fire.storage.ref(noticia.imagem).getDownloadURL().then(url => {
        noticia.imagem = url
        this.noticias.push(noticia)
      })
    console.log(doc.id, '=>', doc.data());
  });
  }
}
</script>

<style>

</style>