<template>

  <header class="contenitore">

    <div class="header-top">
        <div class="header-sinistra">

            <!-- <h1>BOOLFLIX</h1> -->
            <img src="../assets/img/Netflix-Logo.png" alt="">
            <ul>
                <li> <a href="#"> Home </a> </li>
                <li> <a href="#"> Serie TV </a> </li>
                <li> <a href="#"> Film </a> </li>
                <li> <a href="#"> Originali </a> </li>
                <li> <a href="#"> La mia lista </a> </li>
            </ul>

        </div>

        <div class="header-destra">
            <i class="fas fa-search"></i>
            <input 
            type="text" 
            placeholder="Cerca film"
            v-model="cercaFilm"
            @keypress.enter="cerca">  

            <i class="fas fa-bell"></i>

            <img class="avatar" src="../assets/img/Netflix-avatar.png" alt="">

            <div class="cerchio"></div>

        </div>

    </div>


    <div class="jumbotrone">
        <img src="../assets/img/Venom-logo.png" alt="">
        <div class="didascalia">
            <p>
                Dopo aver trovato un corpo ospite nel giornalista investigativo Eddie Brock, il simbionte alieno dovrà affrontare un nuovo nemico, Carnage.
            </p>
            <button> <i class="fas fa-play"></i> Riproduci </button>
            <button class="btn-lista"> <i class="fas fa-check"></i> Aggiungi alla lista </button>
        </div>
    </div>

  </header>

</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            cercaFilm: '',
        }
    },
    methods: {
        cerca(){
            console.log('Header.vue fa partire un evento collegato alla stringa scritta nel input', this.cercaFilm);
            this.$emit('nuovaRicerca', this.cercaFilm);
            
        }
    }
}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

header{
    padding-top: 30px;
    .header-top{
        @include center(between);
        .header-sinistra{
            @include center(sinistra);

            a:hover{
                color: red;
            }

            img{
                margin-right: 20px;
                width: 130px;
            }
        }
        .header-destra{
            @include center(destra);
            position: relative;
            input{
                padding: 3px;
                width: 200px;
            }
            i{
                color: white;
                font-size: 17px;
                margin-right: 15px;
            }
            .fa-bell{
                margin-left: 15px;
            }

            .avatar{
                height: 30px;
                width: 30px;
                border-radius: 3px;
            }
            .cerchio{
                position: absolute;
                top: 5px;
                right: 44px;
                height: 8px;
                width: 8px;
                background-color: red;
                border-radius: 50%;
            }
        }
    }


    h2{
        margin: 50px 0px 15px 0px;
        color: white;
    }

    .jumbotrone{
        @include center(sinistra);
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-end;
        width: 100%;
        height: 530px;
        background-image: url("../assets/img/carnage.jpg" );
        background-position: top;
        background-size: cover;
        border-radius: 20px;
        margin:15px 0px 60px 0px;
        img{
            margin-left: 10px;
            width: 30%;
        }
        .didascalia{
            width: 37%;
            margin: 10px 20px;
            button{
                border: none;
                padding: 5px 50px;
                margin-right: 15px;
                i{
                    margin-right: 5px;
                    font-size: 13px;
                }
            }

            .btn-lista{
                background-color: #5A6369;
                color: white;
                
            }
            
            p{
                border-radius: 10px;
                margin-bottom: 15px;
                width: 85%;
                color: white;
                font-size: 14px;
                font-weight: 200;
                box-shadow: inset 30px 10px 30px black;
                padding: 4px 0px;
            }
        }
    }
}

</style>