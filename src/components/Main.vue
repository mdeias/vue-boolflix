<template>
    <main class="contenitore">

        <h2>Film</h2>
        <div class="row">
            <Card 
            v-for="film in filmDaStampare"
            :key="film.id"
            :titolo="film.title"
            :titoloOriginale="film.original_title"
            :lingua="film.original_language"
            :giudizio="film.vote_average"
            />

        </div>

        <h2>Serie</h2>
        <div class="row">

            <Card 
            v-for="serie in serieDaStampare"
            :key="serie.id"
            :titolo="serie.name"
            :titoloOriginale="serie.original_name"
            :lingua="serie.original_language"
            :giudizio="serie.vote_average"
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

}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

main{
    
    .row{
        margin: 30px 0px;
        overflow:auto ;
        @include center(sinistra);
        height: 290px;
    }
    h2{
        color:white;
    }
}

</style>