<template>
  <table class="w-full text-md bg-white shadow-md rounded mb-4 text-center mt-4 pt-6">
  <thead >
    <tr class="border-b">
      <th class="mr-6">#</th>
      <th>Nombre</th>
      <th>Categorias</th>
      <th>Estado</th>
      <th>Numero</th>
      <th>Accion</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="item in tareas" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.nombre }}</td>
      <td>
          <span v-for="(cat, index) in item.categoria" :key="index">
            {{ (item.categoria.length === index + 1) ? cat : cat + ', ' }}
          </span>
      </td>
      <td>{{ item.estado }}</td>
      <td>{{ item.numero }}</td>
      <td>
        <router-link 
        class="mr-3 text-sm bg-green-500 hover:bg-green-700 text-white py-1 px-2 rounded focus:outline-none focus:shadow-outline"
        :to="{
            name: 'Edit',
            params: {
                id: item.id
            }
        }"
        >Editar
        </router-link>
        <button type="button"  
                class="text-sm bg-red-500 hover:bg-red-700 text-white py-1 px-2 rounded focus:outline-none focus:shadow-outline"
                @click="deleteTareas(item.id)">Delete
        </button>
      </td>
    </tr>
  </tbody>
</table>
</template>

<script>
import { mapActions, mapState } from 'vuex'
export default {
  computed: {
      ...mapState(['tareas'])
  },
  methods: {
      ...mapActions(['deleteTareas'])
  },
}
</script>
