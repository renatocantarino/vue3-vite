<script setup>
import { computed } from 'vue';

const props = defineProps(['books']);

const booksRead = computed(()=> {
    return props.books.filter( it => it.isRead).length;
})

const booksLength = computed(()=> {
    return props.books.length;
})

const booksMessage = computed(()=> {
    return booksRead.value >= booksLength.value 
    ? 'Parabens, você leu todos os livros'
    : `${booksRead.value} de ${booksLength.value}`

})


</script>

<template>
    <div class="books-read">
        <label for="progress">Seu progresso</label> <br />
        <progress :value="booksRead" :max="booksLength"></progress>
        <p>
            {{ booksMessage }}
        </p>
    </div>
</template>
