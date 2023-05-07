<template>
  <div>
    <div class="container">
      <h6 v-for="project in projects" :key="projects.id">
        {{ project.nome_progetto }}
      </h6>
    </div>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  data() {
    return {
      projects: []
    }
  },
  methods: {
    fetchProjects() {
      axios.get('http://127.0.0.1:8000/api/projects').then(res => {
        const { results } = res.data
        this.projects = results
      }).catch(err =>{
        console.log(err)
      })
    }
  },
  mounted(){
    this.fetchProjects()
  }
}

</script>

<style lang="scss" scoped>


</style>