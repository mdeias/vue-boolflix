<template>

  <header class="contenitore">

    <div class="header-top">
        <div class="header-sinistra">

            
            <img class="n-logo-esteso" src="../assets/img/Netflix-Logo.png" alt="">

            <img class="n-mini-logo" src="../assets/img/netflix-mini-logo.svg" alt="">

            <i class="fas fa-bars"></i>

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

            <select
            v-model="selezionaFilmTv"
            @change="filtraContenuti"
            >
                <option value="" selected>All</option>
                <option value="Film">Film</option>
                <option value="Serie">Serie</option>
            </select>

            <i class="fas fa-bell"></i>

            <img class="avatar" src="../assets/img/Netflix-avatar.png" alt="">

            <div class="cerchio">1</div>

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
            selezionaFilmTv: ''
        }
    },
    methods: {
        cerca(){
            console.log('Header.vue fa partire un evento collegato alla stringa scritta nel input', this.cercaFilm);
            this.$emit('nuovaRicerca', this.cercaFilm);
            
        },
        filtraContenuti(){
            console.log('Header invia la value della selezione', this.selezionaFilmTv);
            this.$emit('nuovaSelezione', this.selezionaFilmTv);
        }
    }
}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

header{
    padding-top: 10px;
    .header-top{
        @include center(between);
        .header-sinistra{
            @include center(sinistra);

            a:hover{
                color: red;
            }

            .n-logo-esteso{
                margin-right: 20px;
                width: 130px;
                
            }

            .n-mini-logo{
                width: 20px;
                display: none
            }

            i{
                color: #fff;
                font-size: 20px;
                margin-left: 15px;
                display: none;
            }

        }
        .header-destra{
            @include center(destra);
            position: relative;
            input{
                border-radius: 5px;
                padding: 2px;
                width: 150px;
            }
            select{
                padding: 2px;
                width: 65px;
                margin-left: 15px;
                border-radius: 5px;
                background-color: #fff;
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
                color: white;
                font-size: 5px;
                text-align: center;

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


    @media screen and (max-width:1410px) {
        
        .jumbotrone{           
            img{
                margin: 0;
                width: 50%;
                max-width: 350px;
            }
            .didascalia{
                width: 50%;                
                p{
                    padding: 0px 10px;
                    width: 85%;
                }
                button{
                    margin-right: 5px;
                    margin-left: 5px;
                }
            }
        }
    }

    @media screen and (max-width:1000px){
        .header-top{
            .header-sinistra{                
                ul{
                    display: none;
                      
                }
                i{
                    display: inline-block;
                }
                .n-logo-esteso{
                    display: none;
                }       
                .n-mini-logo{
                    display: inline-block;
                } 
            }
            .header-destra{
                .fa-search{
                    display: none;
                }                
            }

        }
        .jumbotrone{
            @include center();
            justify-content: flex-end;
            img{
                margin: 0;
                width: 60%;
                max-width: 350px;
            }
            .didascalia{
                width: 75%;
                margin: 0px 20px 10px 20px;
                text-align: center;
                p{
                    padding: 0px 10px;
                    margin: 15px;
                    width: 95%;
                }
                button{
                    margin-right: 5px;
                    margin-left: 5px;
                }
            }
        }
    }

    @media screen and (max-width:660px)  {
        .jumbotrone{
            
            .didascalia{
                width: 90%;
                margin: 0px 20px 10px 20px;
                text-align: center;
                p{
                    padding: 0px 10px;
                    margin: 15px;
                    width: 95%;
                }
                .btn-lista{
                    margin-top: 10px;
                }
            }
        }
    }
}
</style>