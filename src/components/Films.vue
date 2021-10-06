<template>
    <div class="movies-container">
        <ul>
            <li v-for="(film, index) in films" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film -->
                <Card :details="film"/>
            </li>
        </ul>
<hr>
        <ul>
            <li v-for="(serie, index) in series" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta la serie -->
                <Card :details="serie"/>
            </li>
        </ul>
    </div>
</template>

<script>
import Card from './Card.vue';

export default {
    name: 'Films',
    props: ['films', 'series'],
    components: {
        Card
    }
}
</script>

<style lang="scss" scoped>

</style>