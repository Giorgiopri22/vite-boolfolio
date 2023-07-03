<script >
import axios from 'axios';
import ProjectSingleCard from "../components/ProjectSingleCard.vue";

  export default{
    components:{
      ProjectSingleCard
    },
    data(){
      return{
        baseUrl : 'http://127.0.0.1:8000',
        projects: [],
        currentPage: 1,
        lastPage: null,
        types: null,
        selectedType: "all",
        technologies: null,
        selectedTechnologies: []
      }
    }, mounted(){
        this.getProjects(1);
        this.getTypes();
        this.getTechnologies();
    },
    watch: {
      selectedTechnologies: {
      handler: 'getProjects',
      deep: true
    }
},
    methods:{

      getTechnologies(){
        axios.get(`${this.baseUrl}/api/technologies`).then(res => {
          this.technologies = res.data.technologies
        })
      },
      
      getTypes(){
        axios.get(`${this.baseUrl}/api/types`

        ).then(res=>{
          this.types = res.data.types
        })
      },
      getProjects(projectApiPage){
          const params = {
          page: projectApiPage
        }

        if(this.selectedType !== 'all'){
          params.type_id = this.selectedType
        }
        if(this.selectedTechnologies.length > 0){
        params.technologies_ids = this.selectedTechnologies.join(',');
      }
        axios.get(`${this.baseUrl}/api/projects`, { params }).then(res=>{
          this.projects=res.data.projects.data
          this.currentPage = res.data.projects.current_page
          this.lastPage = res.data.projects.last_page
        })
      },
    }
  }
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="mb-3">
        <label for="" class="form-label">Tipologia</label>
        <select @change="getProjects()" v-model="selectedType" class="form-select form-select-lg" name="" id="">
          <option value="all"> -- All -- </option>
          <option v-for="(elem, index) in types" :key="index" :value="elem.id">{{elem.name}}</option>
        </select>
      </div>
      <div class="mb-3">
        <h4>Technologies Filter</h4>
        <label for="" v-for="(elem,index) in technologies" :key="index">
          <input type="checkbox" name=""  id="" :value="elem.id" v-model="selectedTechnologies">
          {{ elem.name }}
        </label>
      </div>

      <ProjectSingleCard v-for="(projects,index) in projects " :key="index" :projectProps="projects"/>
    </div>
  </div>

  <nav aria-label="Page navigation example">
    <ul class="pagination">
      <li class="page-item">
        <a class="page-link" @click.prevent="getProjects(currentPage - 1)" href="#" aria-label="Previous">
          <span  aria-hidden="true" >&laquo;</span>
        </a>
      </li>
      <li class="page-item" v-for="(elem,index) in lastPage" :key="index" :class="(currentPage === elem) ? 'active' : ''">
        <a class="page-link" @click.prevent="getProjects(elem)" href="">{{ elem }}</a>
      </li>
      <li class="page-item">
        <a class="page-link" @click.prevent="getProjects(currentPage + 1)" href="#" aria-label="Next">
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>
    </ul>
  </nav>

</template>

<style lang="scss">
@use '../style/main.scss';
</style>
