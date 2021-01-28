<template>
  <ion-router-outlet />

    <form class="label-search">
        <ion-label>Montant: </ion-label>
        <ion-input class="input-color" type="number" v-model="numberToConvert" placeholder="Euro"></ion-input>
    </form>
 

</template>
<style>
  .label-search{
    text-align: left;
  }
  .input-color{
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    border-radius: 2%;
  }
</style>
<script>

import { IonInput, IonRouterOutlet } from '@ionic/vue';



export default ({
  name: 'Search',
  data(){
    return{        
      numberToConvert: '',
    }
  },
  methods: {
  },
  components: {
    IonRouterOutlet,
    IonInput
  }

});
</script>