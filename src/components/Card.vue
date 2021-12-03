<template>
  <div class="card">
        <img :src="`https://image.tmdb.org/t/p/w500${image}`" alt="">
         <h3>Titolo: {{titolo}}</h3>
         <p>
             Titolo Originale: {{titoloOriginale}}
         </p>
         <div>
             <img class="bandiera"
             v-if="this.bandiere.includes(lingua)" 
             :src="require(`../assets/img/${lingua}.png`)"
             :alt="lingua">

            <p v-else>Lingua: {{lingua}}</p>
         </div>
         <p>Voto: {{giudizio}}</p>
     </div>
</template>

<script>

export default {
    name: 'Card',
    props:{

        image: String,
        titolo: String,
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
    @include center();
    align-items: flex-start;
    flex-direction: column;
    // border: 1px solid white;
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
        // display: none;
    }
    h3{
        font-size: 15px;
        margin: 10px 0px 10px 10px;
        // display: none;
    }
    img{
        height: 270px;
        display: none;
    }
    .bandiera{
        border: 1px solid black;
        border-radius: 2px;
        margin-left: 10px;
        width: 20px;
        display: inline-block;
        height: 12px;
    }

}
</style>