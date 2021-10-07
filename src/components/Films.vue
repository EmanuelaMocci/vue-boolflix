<template>
    <div class="movies-container">
        <div class="trailer">
            <section>
                <iframe width="560" height="315" src="https://www.youtube.com/embed/iDvPvqImb-4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </section>
        </div>

        <h2>Film:</h2>
        <ul>
            <li v-for="(film, index) in films" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film -->
                <Card :details="film"/>
            </li>
        </ul>

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
        background-color: rgb(20, 20, 20);
        .trailer{
            section{
                display: flex;
                justify-content: center;
                iframe{
                    width: 80%;
                    height: 700px;
                }
            }
        }
        h2{
            padding: 30px 0 0 30px;
            color: lightgray;
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