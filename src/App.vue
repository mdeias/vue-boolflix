<template>
  <div>
    <Header @nuovaRicerca="cercaContenuto"/>
    <Main/>
  </div>
</template>

<script>
// import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',

  components: {
    Header,
    Main
  },

  data(){
    return{
      apiUrl: "https://api.themoviedb.org/3/movie/550?api_key=abeacf18ff900bf858b6c58ae41300e1",
    }
  },

  methods:{
    cercaContenuto(nome){
       console.log('App.vue ha ricevuto qualcosa da un evento (nuovaRicerca)', nome);
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/utilities.scss';
@import './assets/style/mix.scss';

</style>
