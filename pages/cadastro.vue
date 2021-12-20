<template>
<div id="app">
    
    <Modal
      v-show="isModalVisible"
      @entrar="fazerLogin"
      v-model="senha"
    />
    <div>
      <div class="categoria">
        categoria
        <input v-model="categoria" type="text">
      </div>
      <div class="titulo">
        titulo
        <input v-model="titulo" type="text">
      </div>
      <div class="img">
        <input type="file" name="file" ref="files" />
      </div>
      <div class="descricao">
        descrição
        <input v-model="descricao" type="text">
      </div>
      <button @click="cadastrarNoticia">confirmar</button>
    </div>
  </div>
  
</template>

<script>
import Modal from '../components/Modal.vue';
export default {

  name: 'CadastroPage',
  components:{
    Modal
  },
  data () {
    return{
      isModalVisible: true,
      senha: "",
      titulo: "", 
      categoria:"",
      descricao: ""
    }
    
  },
  methods: {
    
    fazerLogin() {
      if(this.senha == "coxinha"){
        this.isModalVisible = false; 
      }
     
    },
    cadastrarNoticia(){
      var sha1= require('js-sha1')
      let noticia = {
        titulo: this.titulo,
        categoria: this.categoria,
        descricao: this.descricao,
        imagem: this.$refs.files.files[0]
      }
      
      this.$fire.storage.ref().child(sha1('')+'.jpg').put(noticia.imagem).then(res =>{
        noticia.imagem = res.ref.fullPath
        console.log(noticia)
        this.$fire.firestore.collection('noticias').add(noticia).then(ref =>{
          console.log(ref.id)
        })
      })
      
    }
  }
  

}

</script>

