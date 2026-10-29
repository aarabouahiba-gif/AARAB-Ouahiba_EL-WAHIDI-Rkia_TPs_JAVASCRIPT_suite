<script>
export default {
  data() {
    return {
      job: {
        title: '',
        description: '',
        salary: 0,
        experience: 0,
        createdAt: new Date().toISOString().slice(0, 10)
      }
    }
  },
  methods: {
    addJob() {
      fetch('http://localhost:3000/jobs', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(this.job)
      })
        .then(() => this.$router.push('/'))
        .catch(err => console.log(err))
    }
  }
}
</script>

<template>
  <div class="page">
    <h1>Ajouter un emploi</h1>
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
      <button @click="addJob">Enregistrer</button>
    </div>
  </div>
</template>
