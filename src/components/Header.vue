<template>

  <header class="contenitore">
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
    @include center();

    input{
        margin: 50px 20px 50px 0px;
        padding: 5px;
        width: 30%;
    }
    button{
        padding: 5px;
        background-color: #fff;
    }
}

</style>