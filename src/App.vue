<template>
  <div>
    <div v-for="project in projects">
      {{ project.title }}
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name:'App', 
    data(){
      return {
        projects: [],
        url: 'http://127.0.0.1:8000/api',
      }
    },
    methods: {
      pippo(){
        axios.get(`${this.url}/projects`).then((res)=>{
          this.projects = res.data.results.data,
          console.log(this.projects);
        })
      }
    },
    mounted(){
      this.pippo();
    }
  }
</script>

<style lang="scss" scoped>

</style>
