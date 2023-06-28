<script >
import axios from 'axios';

  export default{
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
  <div v-for="(projects,index) in projects " :key="index">
    {{ projects.name }}
    {{ projects.description }}
    <img :src=" `${baseUrl}/storage/${projects.image}`" alt="">
  </div>
</template>

<style lang="scss">
@use './style/main.scss';
</style>
