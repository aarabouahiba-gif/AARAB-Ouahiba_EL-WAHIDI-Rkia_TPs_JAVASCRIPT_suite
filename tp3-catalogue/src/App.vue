<script setup>
import { ref, onMounted } from 'vue'
import BookList from './components/BookList.vue'
import AddBookForm from './components/AddBookForm.vue'

const books = ref([])
const loading = ref(true)

const initialBooks = [
  { id: 1, title: 'Dans le coeur d’une femme', author: 'Khaoula Hamdi', isFav: false },
  { id: 2, title: 'Ma raison de vivre', author: 'Khaoula Hamdi', isFav: true },
  { id: 3, title: 'Le Passé simple', author: 'Driss Chraïbi', isFav: false },
  { id: 4, title: 'La Boîte à merveilles', author: 'Ahmed Sefrioui', isFav: false },
  { id: 5, title: 'Le Pain nu', author: 'Mohamed Choukri', isFav: true }
]

onMounted(() => {
  setTimeout(() => {
    books.value = initialBooks
    loading.value = false
  }, 600)
})

function toggleFav(id) {
  const book = books.value.find(book => book.id === id)
  if (book) book.isFav = !book.isFav
}

function addBook(book) {
  books.value.push({
    id: Date.now(),
    title: book.title,
    author: book.author,
    isFav: false
  })
}
</script>

<template>
  <main>
    <h1>Catalogue de livres</h1>

    <p v-show="loading">Chargement des livres...</p>

    <AddBookForm @add-book="addBook" />

    <BookList
      :books="books"
      @toggle-fav="toggleFav"
    />
  </main>
</template>