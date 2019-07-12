<template>
  <div>
    <h1>Contador</h1>
    <p>{{ nombre }}</p>
    <h2>{{ numero }}</h2>
    <button @click="suma()" v-bind:disabled="checkDisabledSuma">Aumenta</button>
    <button @click="resta()" v-bind:disabled="checkDisabledResta">Resta</button>
    <input type="number" v-model="numero" name="" id="">
  </div>
</template>
<script>
export default {
  data() {
    return {
      nombre: 'Victor',
      numero: 0,
    };
  },
  props: {
    initValue: {
      type: Number,
      default: 0,
    },
    maxValue: {
      type: Number,
      default: 100,
    },
    minValue: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    suma() {
      this.numero = +this.numero + 1;
    },
    resta() {
      this.numero = +this.numero - 1;
    },
    created() {
      this.numero = this.initValue;
    },
  },
  computed: {
    checkDisabledResta() {
      return this.numero <= this.minValue;
    },
    checkDisabledSuma() {
      return this.numero >= this.maxValue;
    },
  },
  watch: {
    numero(nuevoValor) {
      if (nuevoValor > this.maxValue) {
        this.numero = this.maxValue;
      } else if (nuevoValor < this.minValue) {
        this.numero = this.minValue;
      }
    },
  },
};
</script>
