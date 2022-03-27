<template>
  <div>
    <h1>Editando la opinion de:</h1>
    <div class="form">
      <div>
        <label>Usuario:</label>
        <input class="form-control" v-model="opinion.usuario.nombre" />
      </div>
      <div>
        <label> Descripcion:</label>
        <textarea class="form-control" v-model="opinion.descripcion">
        </textarea>
      </div>
      <div>
        <button class="btn btn-success mt-2"
         @click="modificarOpinion">Guardar Cambios
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  props: ["id"],
  methods: {
    ...mapActions(["modificar_Opinion"]),
    modificarOpinion() {
      const { opinion } = this;
      this.modificar_Opinion(opinion);
      this.$router.push("/administracion")
    },
  },
  computed: {
    ...mapGetters(["getOpinionById"]),
    opinion() {
      const { id } = this;
      return {
        ...this.getOpinionById(+id),
        usuario: { ...this.getOpinionById(+id).usuario },
      };
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
