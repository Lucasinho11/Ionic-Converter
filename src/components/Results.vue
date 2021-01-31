<template>
  <ion-router-outlet />
   <ion-card>
    <ion-card-header>
      <ion-card-title>Résultat: {{ this.result }}</ion-card-title>
    </ion-card-header>
  </ion-card>

</template>
<style>

</style>
<script>

import {IonRouterOutlet, IonCard, IonCardHeader, IonCardTitle} from '@ionic/vue';

export default ({
  name: 'Results',
  data(){
    return{        
      
    }
  },
  props : ['result'],
  methods: {
  },
  components: {
    IonRouterOutlet,
    IonCard,
    IonCardHeader,
    IonCardTitle
  },

});

</script>