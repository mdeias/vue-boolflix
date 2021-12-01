<template>
  <div class="card">
         <h3>{{titolo}}</h3>
         <p>{{titoloOriginale}}</p>
         <p>{{lingua}}</p>
         <p>{{giudizio}}</p>
     </div>
</template>

<script>

export default {
    name: 'Card',
    props:{
        titolo: String,
        titoloOriginale: String,
        lingua: String,
        giudizio: String
    }

}

</script>

<style lang="scss">
@import '../assets/style/general.scss';
@import '../assets/style/utilities.scss';
@import '../assets/style/mix.scss';

.card{
    @include center();
    flex-direction: column;
    p{
        margin: 10px 0px 5px 0px;
    }
}
</style>