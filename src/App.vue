<script setup>
import { reactive, ref } from 'vue';
import Books from './components/Books.vue';
import Progress from './components/Progress.vue';
import Book from './components/Book.vue';

let books = reactive([
  {
    id: 1,
    title: 'History of Europe',
    cover:
      'https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-6-540x861.jpg',
    isRead: true,
    isbn: '0-395-07157-8',
    author: 'Daniel Trejo',
  },
  {
    id: 2,
    title: 'Penguin Classics',
    cover:
      'https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-2-540x861.jpg',
    isRead: false,
    isbn: '0-395-07157-8',
    author: 'Daniel Trejo, Jon Snow',
  },
  {
    id: 3,
    title: 'Becoming',
    cover:
      'https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-7-540x861.jpg',
    isRead: false,
    isbn: '0-395-07157-8',
    author: 'Daniel Trejo',
  },
  {
    id: 4,
    title: 'Sonnets',
    cover:
      'https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-5-540x861.jpg',
    isRead: false,
    isbn: '0-395-07157-8',
    author: 'Daniel Trejo',
  },
]);

let showNew = ref(false);

function addBook(bookModel) {
  bookModel.id = Math.max(...books.map((el) => el.id)) + 1;
  books.push(bookModel);
  showNew.value = false;
}

function toggeIsRead(id) {
  books.forEach((item) => {
    if (item.id === id) {
      item.isRead = !item.isRead;
    }
  });
}
</script>

<template>
  <div v-if="!showNew" class="container">
    <h1>📖 Meus Livros</h1>
    <div class="header-btns">
      <button @toggeClose="toggeIsRead" @click="showNew = true" class="btn">
        Adicionar Livro +
      </button>
    </div>

    <div class="books-container">
      <Books @toggeIsRead="toggeIsRead" :books="books" />
      <Progress :books="books" />
    </div>
  </div>
  <div v-else class="container">
    <Book @add="addBook" @toggeClose="showNew = false" />
  </div>
</template>
