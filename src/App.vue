<template>
  <div>
    <Header @nuovaRicerca="cercaContenuto" @nuovaSelezione="selezionaContenuto"/>
    <Main :filmDaStampare="arrayFilm" :serieDaStampare="arraySerieTv" :selezioneUtente="contenutoSelezionato"/>
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
      arraySerieTv: [],
      contenutoSelezionato: "",
    }
  },

  methods:{
    cercaContenuto(nome){
       console.log('App.vue ha ricevuto qualcosa da un evento (nuovaRicerca)', nome);
       
       if (this.contenutoSelezionato === "Film") {
         axios.get(`${this.apiUrl}movie?query=${nome}&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
       .then(response => {
         console.log('Risposta API film', response);
         this.arrayFilm = response.data.results;
         this.arraySerieTv = [];
         console.log(this.arrayFilm);
       }).catch(errore =>{
         console.log(errore);
       });
       }

       else if (this.contenutoSelezionato === "Serie") {
         axios.get(`${this.apiUrl}tv?query=${nome}&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
       .then(response => {
         console.log('Risposta API serie', response);
         this.arraySerieTv = response.data.results;
         this.arrayFilm = [];
         console.log(this.arraySerieTv);
       }).catch(errore =>{
         console.log(errore);
       });
       }

       else if (this.contenutoSelezionato === "") {
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

    selezionaContenuto(selezione){
      this.contenutoSelezionato = selezione;
       console.log('App.vue ha ricevuto qualcosa da un evento (nuovaSelezione)', this.contenutoSelezionato);
    },

    
  },

  

  mounted(){

    axios.get(`https://api.themoviedb.org/3/discover/movie/?certification_country=IT&certification=R&sort_by=vote_average.desc&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
    .then(response => {
      console.log('Risposta API film', response);
      this.arrayFilm = response.data.results;
      console.log(this.arrayFilm);
    }).catch(errore =>{
      console.log(errore);
    });

    axios.get(`https://api.themoviedb.org/3/discover/tv?with_genres=18&sort_by=vote_average.desc&vote_count.gte=10&api_key=abeacf18ff900bf858b6c58ae41300e1&language=it-IT`)
    .then(response => {
      console.log('Risposta API serie', response);
      this.arraySerieTv = response.data.results;
      console.log(this.arraySerieTv);
    }).catch(errore =>{
      console.log(errore);
    });
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
@import './assets/style/utilities.scss';
@import './assets/style/mix.scss';

</style>
