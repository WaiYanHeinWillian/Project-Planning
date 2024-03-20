<template>
  <h1>Home</h1>
  <div class="home">
    <div v-for="project in projects" v-bind:key="project.id">
      <SingleProject v-bind:projectly="project" v-on:deleting="deleteProject" @updCompProj="CompProject"></SingleProject>
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

  methods:{
    deleteProject(id){
      this.projects=this.projects.filter(loopProject=>{
        return loopProject.id!=id;
      })
    },

    CompProject(ids){
      let ComPro=this.projects.find(lopComPro=>{
        return lopComPro.id===ids
      });
      ComPro.complete=!ComPro.complete;
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
