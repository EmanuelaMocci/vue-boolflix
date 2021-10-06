<template>
    <div class="movies-container">
        <ul>
            <li v-for="(film, index) in films" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film -->
                <Card :details="film"/>
            </li>
        </ul>
    </div>
</template>

<script>
import Card from './Card.vue';

export default {
    name: 'Films',
    props: ['films'],
    components: {
        Card
    }
}
</script>

<style lang="scss" scoped>

</style>