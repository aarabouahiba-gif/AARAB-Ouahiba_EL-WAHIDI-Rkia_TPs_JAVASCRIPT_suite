<script>
import BookCard from './BookCard.vue'

export default {
  components: { BookCard },
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  emits: ['toggle-fav']
}
</script>

<template>
  <div>
    <BookCard
      v-for="book in books"
      :key="book.id"
      :book="book"
      @toggle-fav="$emit('toggle-fav', $event)"
    >
      <template #actions>
        <small>Mon catalogue</small>
      </template>
    </BookCard>
  </div>
</template>