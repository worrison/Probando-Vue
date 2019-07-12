<template>
  <div>
    <h1>Todos</h1>
    <Counter :initValue="5"></Counter>
  </div>
</template>
<script>
import Counter from '../components/Counter.vue';

export default {
  data() {
    return {
      nombre: 'Victor',
    };
  },
  components: {
    Counter,
  },
};
</script>
