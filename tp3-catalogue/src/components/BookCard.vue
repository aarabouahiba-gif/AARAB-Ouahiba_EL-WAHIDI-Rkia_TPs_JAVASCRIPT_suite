<script setup>
defineProps({
  book: {
    type: Object,
    required: true,
    validator: book => book.title && book.title.trim() !== ''
  }
})

defineEmits(['toggle-fav'])
</script>

<template>
  <div>
    <h3>{{ book.title }}</h3>
    <p>{{ book.author }}</p>

    <p v-if="book.isFav">Favori</p>

    <button @click="$emit('toggle-fav', book.id)">
      {{ book.isFav ? 'Retirer des favoris' : 'Ajouter aux favoris' }}
    </button>

    <slot name="actions"></slot>
  </div>
</template>