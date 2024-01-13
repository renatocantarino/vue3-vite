<script setup>
let bookModel = {
  title: '',
  cover: '',
  isRead: false,
  isbn: '',
  author: '',
};
</script>

<template>
    <div>
        <h1>📖 Adicionar Livro</h1>
        <div class="header-btns">
            <button @click="$emit('toggeClose')" class="btn">Fechar x</button>
        </div>

        <form class="add-form">
            <div class="form-control">
                <label>Título</label>
                <input type="text" v-model="bookModel.title" name="text" placeholder="Adicione o título" required />
            </div>
            <div class="form-control">
                <label>Capa</label>
                <input type="text" name="cover" v-model="bookModel.cover" placeholder="Adicione o link da imagem de capa"
                    required />
            </div>
            <div class="form-control">
                <label>Autor</label>
                <input type="text" v-model="bookModel.author" name="author" placeholder="Adicione o autor" required />
            </div>
            <div class="form-control">
                <label>ISBN#</label>
                <input type="text" v-model="bookModel.isbn" name="isbn" placeholder="Adicione o ISBN" />
            </div>
            <div class="form-control form-control-check">
                <input type="checkbox" v-model="bookModel.isRead" name="readIt" id="readIt" />
                <label for="readIt">Já li o livro</label>
            </div>

            <button type="submit" @click.prevent="$emit('addBook', bookModel)" class="btn btn-block">
                Salvar livro
            </button>
        </form>
    </div>
</template>
