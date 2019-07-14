<template>
  <div id="app" class="container-fluid">
    <div id="nav" class="navbar navbar-expand-lg navbar-light bg-dark">
      <router-link to="/" class="nav-link ">Home</router-link> |
      <router-link to="/tareas" class="nav-link">Tareas</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: white;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
