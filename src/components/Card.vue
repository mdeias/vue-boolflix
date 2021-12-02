<template>
  <div class="card">
        <img :src="`https://image.tmdb.org/t/p/w500${image}`" alt="">
         <h3>Titolo: {{titolo}}</h3>
         <p>
             Titolo Originale: {{titoloOriginale}}
         </p>
         <p>Lingua: {{lingua}}</p>
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
    border: 2px solid red;
    padding:15px;
    margin: 20px 1px;
    flex-basis: 180px;
    flex-grow: 0;
    flex-shrink: 0;
    height: 270px;
    background-color: gray;
    p{
        margin: 10px 0px 5px 0px;
        font-size: 12px;
    }
    h3{
        font-size: 15px;
    }
}
</style>