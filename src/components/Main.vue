<template>
    <main class="contenitore">

        <div class="row" v-if="filmDaStampare.length > 0">
        <h2>Film</h2>

            <Card 
            v-for="film in filmDaStampare"
            :key="film.id"
            :image="film.poster_path"
            :titolo="film.title"
            :titoloOriginale="film.original_title"
            :lingua="film.original_language"
            :giudizio="film.vote_average"
            :descrizione="film.overview"
            />

        </div>

        <div class="row" v-if="serieDaStampare.length > 0">
        <h2>Serie</h2>

            <Card 
            v-for="serie in serieDaStampare"
            :key="serie.id"
            :image="serie.poster_path"
            :titolo="serie.name"
            :titoloOriginale="serie.original_name"
            :lingua="serie.original_language"
            :giudizio="serie.vote_average"
            :descrizione="serie.overview"
            />

        </div>
    </main>
</template>

<script>

import Card from './Card.vue';

export default {

    name: 'Main',

    components:{
        Card
    },

    props:{
        filmDaStampare: Array,  
        serieDaStampare: Array  
    },

    data(){
        return{
           
           bandiere: ['it', 'en']
        }
    },


}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

main{
    
    .row{
        margin: 30px 0px;
        overflow:auto;
        @include center(sinistra);
        height: 400px;
        position: relative;
    }
    h2{
        position: absolute;
        color:white;
        top: 0;
        left: 0;
    }
}

</style>