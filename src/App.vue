<template>
  <nav>
    <router-link to="/" class="home">Home</router-link>
    
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #2c3e50;
}

.home{
  text-decoration: none;
  font-weight: bold;
  color: black;
}

</style>
