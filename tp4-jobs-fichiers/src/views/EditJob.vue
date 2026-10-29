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
    updateJob() {
      fetch('http://localhost:3000/jobs/' + this.job.id, {
        method: 'PATCH',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(this.job)
      })
        .then(() => this.$router.push('/jobs/' + this.job.id))
        .catch(err => console.log(err))
    }
  }
}
</script>

<template>
  <div class="page" v-if="job">
    <h1>Modifier l'emploi</h1>
    <div class="card">
      <label>Titre</label><br />
      <input v-model="job.title" /><br />
      <label>Description</label><br />
      <textarea v-model="job.description"></textarea><br />
      <label>Salaire</label><br />
      <input type="number" v-model.number="job.salary" /><br />
      <label>Années d'expérience</label><br />
      <input type="number" v-model.number="job.experience" /><br />
      <label>Date de création</label><br />
      <input type="date" v-model="job.createdAt" /><br /><br />
      <button @click="updateJob">Mettre à jour</button>
    </div>
  </div>
</template>
