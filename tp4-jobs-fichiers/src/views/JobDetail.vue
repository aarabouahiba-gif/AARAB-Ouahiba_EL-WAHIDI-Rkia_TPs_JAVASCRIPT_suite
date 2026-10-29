<script>
export default {
  data() {
    return { job: null }
  },
  mounted() {
    fetch('http://localhost:3000/jobs/' + this.$route.params.id)
      .then(response => response.json())
      .then(data => (this.job = data))
      .catch(err => console.log(err))
  },
  methods: {
    deleteJob() {
      if (!confirm('Voulez-vous vraiment supprimer cet emploi ?')) return
      fetch('http://localhost:3000/jobs/' + this.job.id, { method: 'DELETE' })
        .then(() => this.$router.push('/'))
        .catch(err => console.log(err))
    }
  }
}
</script>

<template>
  <div class="page" v-if="job">
    <div class="card">
      <h1>{{ job.title }}</h1>
      <p>{{ job.description }}</p>
      <p>Salaire : {{ job.salary }} MAD</p>
      <p>Expérience requise : {{ job.experience }} an(s)</p>
      <p>Date de création : {{ job.createdAt }}</p>

      <RouterLink :to="'/jobs/' + job.id + '/edit'"><button>Modifier</button></RouterLink>
      <button class="danger" @click="deleteJob">Supprimer</button>
    </div>
  </div>
</template>
