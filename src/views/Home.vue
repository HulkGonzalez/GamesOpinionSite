<template>
  <div class="home">
    <h1>Lista de Juegos Disponibles</h1>

      <div class="container">
        <div class="row">
      <div class="col-12  col-md-4" v-for="(juego, i) in juegos" :key="i">
         <div  class="card" >
        <img :src="(`${juego.background_image}`)" class="card-img-top" style="max-height: 12rem"  />
        <div class="card-body">
          <h5 class="card-title">{{ juego.name }}</h5>
          <p class="card-text" >
            <ul class="list-group list-group-flush">
              <li class="list-group-item">Id: {{ juego.id }}</li>
              <li class="list-group-item">Rating: {{ juego.rating }}</li>
              <li class="list-group-item">Released: {{ juego.released }}</li>
              <li class="list-group-item">Updated: {{ juego.updated }}</li>
            </ul> 
          </p>
          <button
            @click="juegoSelected = juego.id"
            data-bs-toggle="modal"
            data-bs-target="#exampleModal"
            class="btn btn-primary">Opinar
          </button>
        </div>
      </div>
      </div>
     
    </div>
      </div>

    <!-- Modal -->
    <div class="modal fade" id="exampleModal">
      <div class="modal-dialog">
        <div class="modal-body">
          <div class="modal-content p-2">
            <h5>Escribe tu opinion para el juego: {{ juego_Selected.name }} </h5>
            <hr />
            <div>
              <label>Nombre:</label>
              <input v-model="opinion.usuario.nombre" class="form-control" placeholder="Tu nombre debe ir aqui"/>
            </div>
            <div>
              <label>Opinion:</label>
              <textarea v-model="opinion.descripcion" class="form-control" placeholder="Tu opinion debe ir aqui"
              ></textarea>
            </div>
            <div class="mt-3">
              <button
               data-bs-toggle="modal"
               data-bs-target="#exampleModal"
               @click="agregarOpinion" 
               class="btn btn-primary">Agregar
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations, mapGetters } from "vuex";
export default {
  name: "Home",
  methods: {
    ...mapMutations(["AGREGAR_OPINION"]),
    agregarOpinion() {
      const { juegoSelected } = this;
      const opinion = {
        ...this.opinion,
        usuario: { ...this.opinion.usuario },
      };
      opinion.idJuego = juegoSelected;
      opinion.id = Math.floor(Math.random() * 999);
      this.AGREGAR_OPINION(opinion);
      // Limpiar formulario
      this.opinion.usuario = { nombre: "" };
      this.opinion.descripcion = "";
    },
  },
  data() {
    return {
      juegoSelected: null,
      opinion: {
        usuario: {
          nombre: "",
        },
        descripcion: "",
      },
    };
  },
  computed: {
    ...mapState(["juegos", "opiniones"]),
    ...mapGetters(["getJuegosAndOpiniones", "getJuegoById"]),
    juego_Selected() {
      const { juegoSelected } = this;
      return this.getJuegoById(juegoSelected) || {};
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