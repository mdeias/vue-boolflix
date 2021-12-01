<template>
  <main class="contenitore">
     <Card 
     v-for="film in filmDaStampare"
     :key="film.id"
     :titolo="film.title"
     :titoloOriginale="film.original_title"
     :lingua="film.original_language"
     :giudizio="film.vote_average"
     />
  </main>
</template>

<script>

import Card from './Card.vue'

export default {

    name: 'Main',

    components:{
        Card
    },

    props:{
        filmDaStampare: Array,
        film: Object
    },

    methods:{

    }
}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

main{
    @include center(sinistra);
    flex-wrap: wrap;
    
}

</style>