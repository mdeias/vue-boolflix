<template>
    <main class="contenitore">

        <h2 v-if="filmDaStampare.length > 0">Film</h2>
        <div class="row" v-if="filmDaStampare.length > 0">

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

        <h2 v-if="serieDaStampare.length > 0">Serie TV</h2>
        <div class="row" v-if="serieDaStampare.length > 0">

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
        serieDaStampare: Array,
        selezioneUtente: String  
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
        margin: 0px 0px 35px 0px;
        overflow:auto;
        @include center(sinistra);
        height: 350px;
        position: relative;
    }
    h2{
        
        color:white;
        
    }
}

</style>