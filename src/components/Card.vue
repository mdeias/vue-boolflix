<template>
    <div class="card">

        <div class="card__face card__face--front">

        <img v-if="this.poster" :src="`https://image.tmdb.org/t/p/w500${image}`" alt="">
        <h1 v-else >{{titolo}}</h1>
        
        </div>

        <div class="card__face card__face--back">
            
            <h3><span>Titolo:</span> {{titolo}}</h3>
            <p>
                <span>Titolo Originale:</span> {{titoloOriginale}}
            </p>
            <div>
                <img class="bandiera"
                v-if="this.bandiere.includes(lingua)" 
                :src="require(`../assets/img/${lingua}.png`)"
                :alt="lingua">
                <p v-else><span>Lingua:</span> {{lingua}}</p>
            </div>
            <div class="giudizio">
                <i
                v-for="(icon, index) in 5"
                :key="index"
                class="fa-star"
                :class="index < Math.round(giudizio/2) ? 'fas' : 'far' ">
                </i>
            </div>
            <div class="descrizione">
                <p>
                    {{descrizione}}
                </p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Card',
    props:{

        image: String,
        titolo: String,
        descrizione: String,
        titoloOriginale: String,
        lingua: String,
        giudizio: Number
    },
    data(){
        return{
            bandiere: ['it', 'en'],
            poster: this.image
            
        }
    }

}

</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

  .card {
    
    flex-basis: 200px;
    flex-grow: 0;
    flex-shrink: 0; 
    position: relative;
    margin-right: 2px;
    height: 300px;
    color: white;
    cursor: pointer;
    transition: 1s ease-in-out;
    transform-style: preserve-3d;
    

    &:hover {
      transform: rotateY(0.5turn);
    }

    .card__face--front{
        position: relative;
        h1{
            width: 180px;
            border-top: 1px solid red;
            font-size: 20px;
            padding-top: 60px;
            padding-right: 55px;
            position: absolute;
            top: 0px;
            left: 10px;
        }
    }

    .card__face--back{
        background-color: black;
        padding: 10px;
        width: 200px;
        height: 300px;
        overflow: hidden;
        p{
            margin: 10px 0px;
            font-size: 12px;
            color: white;
        }
        h3{
            color: white;
            font-size: 15px;
            margin: 10px 0px;
            span{
                color: red;
            }
        }
        .bandiera{
            border: 1px solid black;
            border-radius: 2px;
            
            width: 20px;
            display: inline-block;
            height: 12px;
            
        }
        .giudizio{           
            i{
                font-size: 10px;
                margin-right: 2px;
                color: gold;
            }
        }
        .descrizione{
            overflow: auto;
            height: 110px;
            margin-top: 10px;
            
        }

        p{
            span{
                color: red;
                font-size: 13px;
                font-weight: 600;
            }
        }
       
    }

    .card__face {
      position: absolute;
      top: 0;
      left: 0;
      backface-visibility: hidden;
      transition: 1s ease-in-out;
      -webkit-box-reflect: below 0
        linear-gradient(transparent, transparent, rgba(0, 0, 0, 0.4));

      img {
        height: 300px; 
      }

      &--back {
        transform: rotateY(0.5turn);
      }
    }
  }

</style>