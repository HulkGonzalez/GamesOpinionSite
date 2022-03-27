<template>
  <div>
    <h1>Administracion lista de opiniones</h1>
  <div class="container" v-if="existenOpiniones">
    <div class="alert alert-danger">
      No existen opiniones por administar
    </div>
  </div>
    <table v-else class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Usuario</th>
          <th>Juego</th>
          <th>Opinion</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(opinion, i) in getJuegosAndOpiniones" :key="i">
          <td>{{ opinion.id }}</td>
          <td>{{ opinion.usuario.nombre }}</td>
          <td>{{ opinion.juego.name }}</td>
          <td>{{ opinion.descripcion }}</td>
          <td>
            <button
              @click="eliminar_Opinion(opinion.id)"
              class="btn btn-danger mx-2"> Eliminar </button>
            <button
              @click="irAEditarOpinion(opinion.id)"
              class="btn btn-info mx-2"> Editar </button>
            
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  computed: {
    ...mapGetters(["getJuegosAndOpiniones"]),
    existenOpiniones(){
      return !this.getJuegosAndOpiniones.length
    }
  },
  methods: {
    ...mapActions(["eliminar_Opinion"]),
    irAEditarOpinion(id) {
      this.$router.push(`/editar/${id}`);
    },
  },
};
</script>

<style scoped>
h1 {
  margin-top: 2%;
  margin-bottom: 2%;
}
</style>