<template>
  <div>
    <Header @nuovaRicerca="cercaContenuto"/>
    <Main :filmDaStampare="arrayFilm" :serieDaStampare="arraySerieTv"/>
  </div>
</template>

<script>
import axios from 'axios';
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
      apiUrl: "https://api.themoviedb.org/3/search/",
      arrayFilm: [],
      arraySerieTv: []
    }
  },

  methods:{
    cercaContenuto(nome){
       console.log('App.vue ha ricevuto qualcosa da un evento (nuovaRicerca)', nome);

       axios.get(`${this.apiUrl}movie?query=${nome}&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
       .then(response => {
         console.log('Risposta API film', response);
         this.arrayFilm = response.data.results;
         console.log(this.arrayFilm);
       }).catch(errore =>{
         console.log(errore);
       });

       axios.get(`${this.apiUrl}tv?query=${nome}&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
       .then(response => {
         console.log('Risposta API serie', response);
         this.arraySerieTv = response.data.results;
         console.log(this.arraySerieTv);
       }).catch(errore =>{
         console.log(errore);
       });
    }
  },

  
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/utilities.scss';
@import './assets/style/mix.scss';

</style>
