<template>
  <!-- <nav>
    <router-link to="/">Home</router-link>    
  </nav> -->
  <NavBar></NavBar>
  <router-view/>
</template>

<script>

import NavBar from './components/NavBar.vue'

export default{
  components:{
    NavBar:NavBar,
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #2c3e50;
}

/* .home{
  text-decoration: none;
  font-weight: bold;
  color: black;
} */

</style>
