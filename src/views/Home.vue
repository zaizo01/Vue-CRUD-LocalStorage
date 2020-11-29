<template>
  <form @submit.prevent="procesarFormulario">
    <div class="m-6">
     <Input :tarea="tarea"/>
    </div>
  </form>
     <Table />
     
</template>

<script>
import Input from '../components/Input.vue'
import Table from '../components/ListaTareas.vue';
import { mapActions } from 'vuex';
import Vue from 'vue'
const shortid = require('shortid');

export default {
  name: 'Home',
  components: {
   Input,
   Table
  },
   data() {
    return {
       tarea: {
         id: '',
         nombre: '',
         categoria: [],
         estado: '',
         numero: 0,
         activo: true
       }
    }
  },
  methods: {
   ...mapActions(['setTareas']),
   procesarFormulario(){
     if (this.tarea.nombre.trim() === '') {
       console.log('Campo vacio');
       
       return;
     }
     console.log('No esta Vacio');

     // Generar ID
     this.tarea.id = shortid.generate();
     console.log(this.tarea.id);

     //Envio de datos
     this.setTareas(this.tarea);

     // Limpiar Datos
     this.tarea = {
         id: '',
         nombre: '',
         categoria: [],
         estado: '',
         numero: 0,
         activo: true
       }
   }
  },
}
</script>
