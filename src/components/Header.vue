<template>
    <div class="header">
            <!-- 1) 'search' nome evento che passo al padre, movie il valore del v-model, tramite il data agganciamo il v-model-->
            <input type="text" placeholder="Inserisci il titolo di un film " v-model="movie">
            <!-- $emit prende due paramentri: il primo è il nome dell'evento, il secondo il paramentro che passiamo -->
            <button @click="$emit('search', movie)">Cerca</button>
    </div>
</template>

<script>

export default {
        name: 'Header',

        data(){
            // 2) In data devo salvare il valore della input (v-model="movie")
            return{
                movie: ""
            }
        }
}

</script>

<style lang="scss" scoped>

.header{
    height: 80px;
    background-color: rgb(20, 20, 20);
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 50px;
    
    input{
        padding: 10px;
        width: 200px;
        height: 20px;
    }
    button{
        padding: 10px;
        height: 44px;
    }
}

</style>
