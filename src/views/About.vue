<template>
  <div class="about">
    <h1>This is an about page</h1>

      <input type="Number" v-model="titulo">
      <p>{{titulo}}</p>
      <textarea v-model="texto"></textarea>
      <button @click="add()">Enviar</button>
    </div>

  
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      titulo : '',
      texto : '',
    }
  },
  methods: {
    add(){
      axios.post('http://localhost:7777/api/practica',{
        titulo : this.titulo,
        texto : this.texto
      }).then(response =>{
        console.log(response.data)
      }).catch(e=>console.log(e))
    }
  },
}
</script>
