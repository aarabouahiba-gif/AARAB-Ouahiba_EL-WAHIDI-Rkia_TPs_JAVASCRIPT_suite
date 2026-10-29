<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['add-book'])

const title = ref('')
const author = ref('')
const titreInput = ref(null)

onMounted(() => {
  titreInput.value.focus()
})

function submitForm() {
  if (!title.value.trim() || !author.value.trim()) return

  emit('add-book', {
    title: title.value.trim(),
    author: author.value.trim()
  })

  title.value = ''
  author.value = ''
  titreInput.value.focus()
}
</script>

<template>
  <form @submit.prevent="submitForm">
    <input
      ref="titreInput"
      v-model="title"
      placeholder="Titre du livre"
      required
    />

    <input
      v-model="author"
      placeholder="Auteur"
      required
    />

    <button type="submit">Ajouter un livre</button>
  </form>
</template>