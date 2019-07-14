<template>
  <div>
    <input type="text" v-model="nuevaFruta" @keyup.enter="addTarea" />
    <input type="number" v-model="cantidad" />
    <span>Completado
    <input type="checkbox" v-model="completado" name="" id=""></span>
    <button @click="addTarea">Add</button>

    <div id="contenedor-listado-tareas" class="d-flex flex-row flex-wrap">
          <div class="card" style="width: 18rem;" v-for="fruta of frutas" :key="fruta.id" :class="{'bg-info' : fruta.completado , 'bg-danger' :!fruta.completado}">
            <img
              src="https://static01.nyt.com/images/2015/09/10/us/motherlode-homework-study/motherlode-homework-study-superJumbo.jpg"
              class="card-img-top"
              alt="..."
            />
            <div class="card-body">
              <h5 class="card-title">{{fruta.nombre}}</h5>
              <p class="card-text">{{fruta.cantidad}}</p>
              <a href="#" class="btn btn-primary">Completar</a>
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
      frutas: [
        { nombre: "pera", cantidad: 10  , completado: false},
        { nombre: "sandia", cantidad: 10 ,completado: true},
        { nombre: "platano", cantidad: 10 , completado:true }
      ],
      nuevaFruta: "",
      cantidad: 0
    };
  },
  methods: {
    addTarea() {
      this.frutas.push({
        nombre: this.nuevaFruta,
        cantidad: this.cantidad,
        completado:this.completado,
      });
      this.nuevaFruta = "";
    }
  }
};
</script>