
<script>
export default{
   name : 'ProjectSingleCard',
   props:['projectProps'],
    data(){
      return{
        baseUrl : 'http://127.0.0.1:8000',
      }
    }, 
    
}
</script> 


<template>
    <div class="card">
        <img :src="`${baseUrl}/storage/${projectProps.image}`" alt="" class="img-fluid">
        <h5>{{ projectProps.title }}</h5>
        <p>{{ projectProps.description }}</p>

        <p v-if="projectProps.type"><span>{{ projectProps.type.name }}</span></p>

        <ul v-if="projectProps.technologies">
            <li v-for="(technology, i) in projectProps.technologies" :key="i">{{ technology.name }}</li>
        </ul>
    </div>
</template>