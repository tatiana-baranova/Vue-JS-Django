<template>
    <div v-if="num < 3">
        <h1>Hello</h1>
        <p>First</p>
    </div>
    <div v-else-if="num == 3">
        <p>Vue забезпечує легке відстеження дій, зміни HTML структури та оновлення інформації без перезавантаження сторінки.</p>
    </div>
    <div v-else="">Last block</div>
    <input @input="this.num = $event.target.value" />
    <button @click="this.isVisible = !this.isVisible">Click</button>
    <div v-if="isVisible">Hi</div>

    <p>
        {{ books[1].author }}
    </p>

    <ul>
        <li v-for="(book, index) in books" v-bind:key="index">
            {{ index +1 }} - {{ book.title }} - <b>{{ book.author }}</b> / <em>{{ book.genre }}</em>
        </li>
    </ul>
</template>

<script>
export default {
    data(){
        return {
            num: 5,
            isVisible: false,
            books: [
                {
                    title: "1984",
                    author: "Джордж Орвелл",
                    year: 1949,
                    genre: "Антиутопія",
                    isAvailable: true
                },
                {
                    title: "Тигролови",
                    author: "Іван Багряний",
                    year: 1944,
                    genre: "Пригодницький роман",
                    isAvailable: false
                },
                {
                    title: "Інтернат",
                    author: "Сергій Жадан",
                    year: 2017,
                    genre: "Сучасна проза",
                    isAvailable: true
                }
            ]
        }

    },
    methods:{
    },
    computed:{
    }

};
</script>
<style>

</style>
