<template>
  <ion-router-outlet />

    <form class="label-search">
        <ion-label>Montant: </ion-label>
        <ion-input class="input-color" type="number" v-model="numberToConvert" placeholder="Euro"></ion-input>
    
      <ion-item>
            <ion-label>Monnaie de la conversion</ion-label>
            <ion-select ok-text="Valider"  cancel-text="Annuler" >
              <ion-select-option v-for="data in dataArray" :key="data">{{ data}}</ion-select-option> 
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

import { IonInput, IonItem, IonSelect, IonSelectOption, IonRouterOutlet, IonLabel, IonButton } from '@ionic/vue';
import axios from 'axios';


export default ({
  name: 'Search',
  data(){
    return{        
      numberToConvert: '',
      dataArray: [],
      
    }
  },
  emits: ['selectMoney'],
  methods: {
  },
  components: {
    IonRouterOutlet,
    IonInput,
    IonLabel,
    IonItem,
    IonSelect,
    IonSelectOption,
    IonButton
  },
  mounted(){
    axios
        .get(`http://data.fixer.io/api/symbols?access_key=ed7580a94544bcab96d6d289203df29a`)
        .then((response) =>{
            console.log(response.data);
            this.dataArray = response.data.symbols
            // this.dataArray = Object.keys(response.data.rates).map(function(cle) {
             // return [cle, response.data.rates[cle]];
            //})
            //console.log(this.dataArray.symbols)
            this.$emit('selectMoney', this.dataArray);
           
          //console.log(dataArray);
        })
        .catch(() =>{
            
        });
  }

});
</script>