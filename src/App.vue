<template>
  <div id="app" class="container mt-2">
    <titulo :titulo="titulo"></titulo>
    <hr />
    <div class="row justify-content-center">
      <div class="col-6">
        <div class="jumbotron jumbotron-fluid rounded">
          <div class="container">
            {{ numTareas }}
            <agregarTarea
              :tareas="tareas"
              v-on:incrementarNumTareas="numTareas += $event"
            ></agregarTarea>
            <listaTareas :tareas="tareas"></listaTareas>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import titulo from "./components/Titulo";
import agregarTarea from "./components/NuevaTarea";
import listaTareas from "./components/ListaDeTareas";

export default {
  components: {
    titulo,
    agregarTarea,
    listaTareas
  },
  data() {
    return {
      titulo: "Lista de tareas",
      tareas: [
        {
          texto: "Aprender vue js",
          terminada: false
        },
        {
          texto: "Aprender angular",
          terminada: true
        },
        {
          texto: "Aprender Flutter",
          terminada: false
        }
      ],
      numTareas: 3
    };
  }
};
</script>
