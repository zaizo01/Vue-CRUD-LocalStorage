<template>
  <div class="mx-auto mt-2 pt-10 p-10 w-96 border border-gray-300 rounded-sm  text-center bg-gray-200 shadow-md">
      <input type="text" class="border border-gray-400 mt-3 ml-4 p-3 rounded-sm" placeholder="Ingrese Nombre" v-model.trim="tarea.nombre">
     <div class="flex w-9/12 justify-between p-4 mx-aut space-x-4">
        <div>
          <input type="checkbox" id="check-1" v-model="tarea.categoria" value="JavaScript">
          <label for="check-1">JavaScript</label>
      </div>
      <div>
          <input type="checkbox" id="check-2" v-model="tarea.categoria" value="Node.js">
          <label for="check-2">Node.js</label>
      </div>
      <div>
          <input type="radio" id="radio-1" v-model="tarea.estado" value="Urgente">
          <label for="radio-1">Urgente</label>
      </div>
      <div>
          <input type="radio" id="radio-2" v-model="tarea.estado" value="Relax">
          <label for="radio-2">Relax</label>
      </div>
     </div>
      <div class="flex justify-around space-x-4">
        <input type="number" class="border-2 border-gray-300" v-model.number="tarea.numero">
        <button class="py-3 px-6 bg-blue-600 text-white rounded" type="submit" :disabled="bloquear">Procesar</button>
      </div>
  </div>
</template>

<script>
export default {
    props: {
        tarea: Object
    },
    computed: {
     bloquear(){
       return this.tarea.nombre.trim() === '' ? true : false;
     }
  },
}
</script>

<style>

</style>