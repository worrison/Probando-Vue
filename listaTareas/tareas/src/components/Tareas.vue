<template>
  <div>
    <input type="text" v-model="nuevatarea" @keyup.enter="addTarea" />
    <textarea v-model="descripcion" name id cols="50" rows="1"></textarea>
    <span>
      Completado
      <input type="checkbox" v-model="completado" name id />
    </span>
    <button @click="addTarea">Add</button>

    <div id="contenedor-listado-tareas" class="d-flex flex-row flex-wrap">
      <div
        class="card text-light"
        style="width: 18rem;"
        v-for="tarea of tareas"
        :key="tarea.id"
        :class="{'bg-success' : tarea.completado , 'bg-primary' :!tarea.completado}"
      >
      
        <img v-if="tarea.completado" :src="imagenTerminada"
          class="card-img-top"
          alt="..."
        />
        <img v-else :src="imagenPendiente"
          class="card-img-top"
          alt="..."
        />
        <div class="card-body">
          <h5 class="card-title">{{tarea.nombre}}</h5>
          <p class="card-text">{{tarea.descripcion}}</p>
          <a class="btn btn-danger" @click="borrado(tarea)">X</a>
          <a class="btn btn-dark" @click="changeCompletado(tarea)">Completar</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import tareas from '../listadetareas.js'
export default {
  data() {
    return {
      titulo: "Hola mundo con vue",
      tareas: [...tareas],
      nuevatarea: "",
      descripcion: "",
      completado: false,
      imagenPendiente:'https://static01.nyt.com/images/2015/09/10/us/motherlode-homework-study/motherlode-homework-study-superJumbo.jpg',
      imagenTerminada:'https://tutorasap.com/wp-content/uploads/2015/01/yes-310x206.png',

    };
  },
  methods: {
    addTarea() {
      this.tareas.push({
        nombre: this.nuevatarea,
        descripcion: this.descripcion,
        completado: this.completado
      });
      this.nuevatarea = "";
    },
    borrado(tarea) {
      let index = this.tareas.indexOf(tarea);
      this.tareas.splice(index, 1);
    },
    changeCompletado(tarea) {
      let index = this.tareas.indexOf(tarea);
      if (this.tareas[index].completado) {
        this.tareas[index].completado = false;
      } else {
        this.tareas[index].completado = true;
      }
    }
  },
  computed: {}
};
</script>