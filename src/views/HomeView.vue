<template>
  <h1>Home</h1>
  <FilterNav @filterNavData="curNav=$event" v-bind:curNavRe="curNav"></FilterNav>
  <div class="home">
    <div v-for="project in projects" v-bind:key="project.id">
      <SingleProject v-bind:projectly="project" v-on:deleting="deleteProject" @updCompProj="CompProject"></SingleProject>
    </div>
      {{curNav}}
  </div>
</template>

<script>


import FilterNav from '../components/FilterNav'
import SingleProject from '../components/SingleProject'
export default {
  name: 'HomeView',

  data(){
    return{
      projects:[],
      curNav:'all'
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
    FilterNav,
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
