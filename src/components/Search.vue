<template>
  <ion-router-outlet />

    <form class="label-search">
        <ion-label>Montant: </ion-label>
        <ion-input class="input-color" type="number" v-model="numberToConvert" placeholder="Euro"></ion-input>
    
      <ion-item>
            <ion-label>Monnaie de la conversion</ion-label>
            <ion-select ok-text="Valider" cancel-text="Annuler">
              <ion-select-option value="dos">DOS</ion-select-option>
              <ion-select-option value="lunix">Linux</ion-select-option>
              <ion-select-option value="mac7">Mac OS 7</ion-select-option>
              <ion-select-option value="mac8">Mac OS 8</ion-select-option>
              <ion-select-option value="win3.1">Windows 3.1</ion-select-option>
              <ion-select-option value="win95">Windows 95</ion-select-option>
              <ion-select-option value="win98">Windows 98</ion-select-option>
            </ion-select>
      </ion-item>
      <ion-button type="submit" expand="block">Convertir</ion-button>
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

import { IonInput, IonItem, IonSelect, IonSelectOption, IonRouterOutlet, IonLabel } from '@ionic/vue';



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
    IonInput,
    IonLabel,
    IonItem,
    IonSelect,
    IonSelectOption,
  }

});
</script>