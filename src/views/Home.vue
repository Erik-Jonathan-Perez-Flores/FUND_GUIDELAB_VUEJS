<template>
  <div class="home">
    <HelloWorld msg="Welcome"/>
     <div class="container">
    <div class="row">
    <div v-for = "item of materias">
   
        <div class="col-sm-6 col-md-3">
            <div class="thumbnail">
            <div class="caption">
                <h3>{{item.sigla}}</h3>
                <p>{{item.nombre}}</p>
                <p><a href="#/practicas" class="btn btn-primary" role="button">Button</a></p>
            </div>
            </div>
        </div>
        </div>
    </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import axios from 'axios';

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data(){
      return {
          materias:null

      }
  },
  mounted() {
      this.Materias()
  },
  methods: {
      Materias(){
          axios.get('http://localhost:7777/api/materia')
          .then(response=>{
              console.log(response)
              this.materias = response.data.materia
          }).catch(e=>console.log(e))
      }
  },
}
</script>
