<template>
  <div class="mt-2">
    <ul class="list-group">
      <template v-for="(tarea, index) in tareas">
        <li
          class="list-group-item"
          :key="index"
          :class="{ terminada: tarea.terminada }"
        >
          {{ index }} {{ tarea.texto }}
          <span class="float-right">
            <button
              type="button"
              @click="eliminarTarea(index)"
              class="btn btn-danger fas fa-times"
              style="height: 35px; width: 40px;"
            ></button>
          </span>
          <span class="float-right">
            <button
              type="button"
              @click="tarea.terminada = !tarea.terminada"
              class="btn btn-success fas fa-check mr-1"
              style="height: 35px; width: 40px;"
            ></button>
          </span>
        </li>
      </template>
    </ul>
    <template>
      <a
        @click="eliminarCompletadas"
        class="btn btn-success mt-2"
        tabindex="-1"
        role="button"
        aria-disabled="true"
        >Eliminar tareas completadas</a
      >
    </template>
  </div>
</template>
<script>
export default {
  props: ["tareas"],
  methods: {
    eliminarTarea: function(indice) {
      this.tareas.splice(indice, 1);
    },
    eliminarCompletadas: function() {
      this.tareas = this.tareas.filter(tarea => tarea.terminada == false);
    }
  }
};
</script>

<style>
.terminada {
  color: gray;
  text-decoration: line-through;
}
</style>
