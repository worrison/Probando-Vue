<template>
  <div>
    <h1>Contador</h1>
    <p>{{ nombre }}</p>
    <h2>{{ numero }}</h2>
    <button @click="suma()" v-bind:disabled="checkDisabledSuma">Aumenta</button>
    <button @click="resta()" v-bind:disabled="checkDisabledResta">Resta</button>
    <input
      v-model="numero"
      type="number"
      :maxValue="maxValue" :minValue="minValue"
      :class="{isGreen, isOrange, isRed}"/>
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
    completedPercentage() {
      return 100 * (this.numero - this.minValue) / (this.maxValue - this.minValue);
    },
    isGreen() {
      return this.completedPercentage <= 33;
    },
    isOrange() {
      return this.completedPercentage > 33 && this.completedPercentage <= 66;
    },
    isRed() {
      return this.completedPercentage > 66;
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

<style>
  .disabled {
    background: white;
    border: none;
  }
  .isRed {
    background:red;
  }
  .isGreen {
    background:greenyellow;
  }
  .isOrange {
    background:orange;
  }
</style>
