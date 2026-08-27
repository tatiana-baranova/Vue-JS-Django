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
</template>

<script>
export default {
    data(){
        return {
            num: 5,
            isVisible: false,
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
