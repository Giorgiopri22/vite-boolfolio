<script >
import axios from 'axios';
import ProjectSingleCard from "./components/ProjectSingleCard.vue";

  export default{
    components:{
      ProjectSingleCard
    },
    data(){
      return{
        baseUrl : 'http://127.0.0.1:8000',
        projects: []
      }
    }, mounted(){
        this.getProjects()
    },methods:{
      getProjects(){
        axios.get(`${this.baseUrl}/api/projects` ).then(res=>{
          this.projects = res.data.projects
        })
      }
    }
  }
</script>

<template>
  <div class="container">
    <div class="row">
      <ProjectSingleCard v-for="(projects,index) in projects " :key="index" :projectProps="projects"/>
    </div>
  </div>

</template>

<style lang="scss">
@use './style/main.scss';
</style>
