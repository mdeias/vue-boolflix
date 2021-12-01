<template>
  <main class="contenitore">
     <Card 
     :titolo="filmDaStampare.title"
     :titoloOriginale="filmDaStampare.original_title"
     :lingua="filmDaStampare.original_language"
     :giudizio="filmDaStampare.vote_average"
     />
  </main>
</template>

<script>
// import axios from 'axios';
import Card from './Card.vue'

export default {

    name: 'Main',

    components:{
        Card
    },

    props:{
        filmDaStampare: Object
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
    @include center();
    
    
}

</style>