<template>
  <div class="home">
    <div v-for="project in projects" v-bind:key="project.id">
      <SingleProject v-bind:projectly="project"></SingleProject>
    </div>
  </div>
</template>

<script>


import SingleProject from '../components/SingleProject'
export default {
  name: 'HomeView',

  data(){
    return{
      projects:[],
    }
  },

  components: {
    SingleProject,
    
  },
  mounted(){
    fetch('http://localhost:3000/projects')
    .then((response)=>{
      return response.json();
    })
    .then((datas)=>{
      return this.projects=datas;
    })
    .catch((err)=>{
      console.log(err.message)
    })
  }
}
</script>
