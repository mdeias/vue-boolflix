<template>
  <div class="card">
        <img :src="`https://image.tmdb.org/t/p/w500${image}`" alt="">
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
             <p> <span>Descrizione:</span> {{descrizione}}</p>
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
            bandiere: ['it', 'en']
        }
    }

}

</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

.card{
    @include center(sinistra);
    align-items: flex-start;
    flex-direction: column;
    
    cursor: pointer;
    margin: 0px 2px;
    flex-basis: 180px;
    flex-grow: 0;
    flex-shrink: 0;
    height: 270px;
    background-color: grey;
    p{
        margin: 10px 0px 10px 10px;
        font-size: 12px;
        display: none;
    }
    h3{
        font-size: 15px;
        margin: 10px 0px 10px 10px;
        display: none;
    }
    img{
        height: 270px;
        // display: none;
    }
    .bandiera{
        border: 1px solid black;
        border-radius: 2px;
        margin-left: 10px;
        width: 20px;
        display: inline-block;
        height: 12px;
        display: none;
    }

    .giudizio{
        margin: 0px 10px 0px 10px;
        display: none;
        i{
        font-size: 10px;
        margin-right: 2px;
        color: gold;
        }
    }
     .descrizione{
         overflow: auto;
         height: 120px;
         margin-top: 10px;
         display: none;
    }

    p{
        span{
            font-size: 13px;
            font-weight: 600;
        }
    }
}
</style>