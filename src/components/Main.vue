<template>
  <main class="contenitore">
     <div class="card">
         <h3>Titolo</h3>
         <p>Titolo Originale</p>
         <p>Lingua</p>
         <p>Voto</p>
     </div>
  </main>
</template>

<script>
// import axios from 'axios';

export default {

    name: 'Main',

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
    .card{
        @include center();
        flex-direction: column;
        p{
            margin: 10px 0px 5px 0px;
        }
    }
}

</style>