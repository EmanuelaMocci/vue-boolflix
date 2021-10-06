<template>
    <div class="movies-container">
        <h2>Film:</h2>
        <ul>
            <li v-for="(film, index) in films" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film -->
                <Card :details="film"/>
            </li>
        </ul>
<hr>
        <h2>Serie tv:</h2>
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
    .movies-container{
        h2{
            padding: 30px 0 0 30px;
        }
        ul{
            display: flex;
            flex-wrap: wrap;
            li{
                margin: 50px 30px 0 0;
                list-style: none;
            }
        }
    }
</style>