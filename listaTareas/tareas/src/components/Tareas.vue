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
        class="card"
        style="width: 18rem;"
        v-for="tarea of tareas"
        :key="tarea.id"
        :class="{'bg-info' : tarea.completado , 'bg-danger' :!tarea.completado}"
      >
        <img
          src="https://static01.nyt.com/images/2015/09/10/us/motherlode-homework-study/motherlode-homework-study-superJumbo.jpg"
          class="card-img-top"
          alt="..."
        />
        <div class="card-body">
          <h5 class="card-title">{{tarea.nombre}}</h5>
          <p class="card-text">{{tarea.descripcion}}</p>
          <a class="btn btn-danger" @click="borrado(tarea)">X</a>
          <a class="btn btn-primary" @click="changeCompletado(tarea)">Completar</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Hola mundo con vue",
      tareas: [
        { nombre: "Crear panel", descripcion: "prueba", completado: false },
        { nombre: "menu", descripcion: "prueba", completado: true },
        { nombre: "contenido", descripcion: "prueba", completado: true }
      ],
      nuevatarea: "",
      descripcion: "",
      completado: false
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