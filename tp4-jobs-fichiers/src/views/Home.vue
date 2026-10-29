<script>
import FilterNav from '../components/FilterNav.vue'

export default {
  components: { FilterNav },
  data() {
    return { jobs: [], search: '' }
  },
  computed: {
    filteredJobs() {
      return this.jobs.filter(j =>
        j.title.toLowerCase().includes(this.search.toLowerCase())
      )
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs')
      .then(response => response.json())
      .then(data => (this.jobs = data))
      .catch(err => console.log(err))
  }
}
</script>

<template>
  <div class="page">
    <h1>Offres d'emploi</h1>
    <RouterLink to="/add"><button>+ Ajouter un emploi</button></RouterLink>
    <FilterNav @filter="search = $event" />

    <div v-for="job in filteredJobs" :key="job.id" class="card">
      <h3>
        <RouterLink :to="'/jobs/' + job.id">{{ job.title }}</RouterLink>
      </h3>
      <p>Salaire : {{ job.salary }} MAD</p>
    </div>

    <p v-if="filteredJobs.length === 0">Aucun emploi trouvé.</p>
  </div>
</template>
