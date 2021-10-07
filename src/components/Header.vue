<template>
    <div class="header">
        <div class="logo">
            <img src="https://fontmeme.com/permalink/211007/c072857f28ffed69c9266a55183f4c20.png" alt="">
            <ul>
                <li>
                    <a href="#"><strong>Home</strong></a>
                </li>
                <li>
                    <a href="#">Serie Tv</a>
                </li>
                <li>
                    <a href="#">Film</a>
                </li>
                <li>
                    <a href="#">Nuovi e Popolari</a>
                </li>
                <li>
                    <a href="#">La mia lista</a>
                </li>
                <li>
                    <a href="#">Guarda di nuovo</a>
                </li>
            </ul>
        </div>

        <div class="input">
            <!-- 1) 'search' nome evento che passo al padre, movie il valore del v-model, tramite il data agganciamo il v-model-->
            <input type="text" placeholder="Inserisci il titolo di un film " v-model="movie">
            <!-- $emit prende due paramentri: il primo è il nome dell'evento, il secondo il paramentro che passiamo -->
            <button @click.prevent="$emit('search', movie)"><i class="fas fa-search"></i></button>
            <i class="fas fa-bell"></i>
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Netflix-avatar.png" alt="avatar netflix">
            <i class="fas fa-caret-down"></i>
        </div>
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
    justify-content: space-between;
    padding: 0 50px;
    
    .logo{
        display: flex;
        ul{
            display: flex;
            li:first-child a{
                    color: white;
                }
            li{
                list-style: none;
                padding: 0 12px;
                a{
                    color: rgb(192, 191, 191);
                    text-decoration: none;
                    font-family: 'Poppins', sans-serif;
                    font-weight: 300;
                    font-size: 13px;
                }
            }
        }
        img{
            width: 120px;
        }
    }
    .input{
        input{
            padding: 10px;
            width: 200px;
            height: 20px;
            background-color: rgb(20, 20, 20);
            outline: none;
            border: none;
            transition: all .5s;
        }
        ::placeholder{
                color: rgb(207, 206, 206);
        }
        textarea:focus, input:focus {
            color: rgb(207, 206, 206);
        }
        input:focus {
            width: 300px;
            top: 0;
            right: 100%;
            border: 1px solid rgb(207, 206, 206);
        }
        button{
            padding: 10px;
            height: 44px;
            background-color: rgb(20, 20, 20);
            color: rgb(207, 206, 206);
            border: 1px solid rgb(207, 206, 206);
        }
        i{
            padding: 0 15px;
            color: rgb(207, 206, 206);
        }
        img{
            width: 35px;
            vertical-align: middle;
            border-radius: 5px;
        }
    }
}

</style>
