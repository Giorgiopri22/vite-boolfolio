<script >
import axios from 'axios';

  export default{
    name :'SingleProject',
    data(){
      return{
        baseUrl : 'http://127.0.0.1:8000',
        project: null
      }
    }, created(){
        this.getSingleProject()
    },methods:{
      getSingleProject(){
        axios.get(`${this.baseUrl}/api/projects/${this.$route.params.slug}` ).then(res=>{
          if(res.data.success){
            this.project = res.data.project
          }else{
            this.$router.push({name : 'NotFound'} )
          }
        })
      }
    }
  }
</script>

<template>
<h1>{{ project.name }}</h1>
<h2>{{ project.description }}</h2>
<img :src="project.image" alt="">
</template>

<style lang="scss">
@use '../style/main.scss';
</style>
