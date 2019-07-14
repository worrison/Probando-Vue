<template>
<div>
  <h1> Panel de Tareas</h1>
  <Tareas/>
</div>
</template>

<script>
// @ is an alias to /src
import Tareas from '@/components/Tareas.vue';

export default {
  name: 'home',
  components: {
    Tareas,
  },
};
</script>

<style>
  .lists{
    display: flex;
    flex-direction: row;
  }

</style>