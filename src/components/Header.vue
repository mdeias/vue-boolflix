<template>

  <header class="contenitore">
      <h1>BOOLFLIX</h1>
      <input 
      type="text" 
      placeholder="Cerca film"
      v-model="cercaFilm"
      @keypress.enter="cerca">
      />  
  </header>

</template>

<script>
export default {
    name: 'Header',
    data(){
        return{
            cercaFilm: '',
        }
    },
    methods: {
        cerca(){
            console.log('Header.vue fa partire un evento collegato alla stringa scritta nel input', this.cercaFilm);
            this.$emit('nuovaRicerca', this.cercaFilm);
        }
    }
}
</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

header{
    @include center(sinistra);
    position: relative;
    input{
        margin: 30px 0px;
        padding: 4px;
        width: 200px;
        position: absolute;
        right: 0px;
        top: 0px;
    }
    h1{
        margin: 30px 0px;
        color: red;
    }
}

</style>