<script>
export default {
  emits: ['filter'],
  data() {
    return { search: '' }
  }
}
</script>

<template>
  <input
    type="text"
    v-model="search"
    placeholder="Rechercher par titre..."
    @input="$emit('filter', search)"
  />
</template>
