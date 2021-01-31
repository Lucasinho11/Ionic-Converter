<template>
  <ion-router-outlet />

    <form class="label-search" @submit.prevent="toResult">
        <ion-label>Montant: </ion-label>
        <ion-input class="input-color" type="number" v-model="numberToConvert" placeholder="Euro"></ion-input>
      <ion-item>
            <ion-label>Monnaie de la conversion</ion-label>
            <ion-select ok-text="Valider"  cancel-text="Annuler" v-model="selected" >
              <ion-select-option v-for="data in dataArray" :key="data" :value="data[1]">{{ data[0] }}</ion-select-option> 
            </ion-select>
      </ion-item>
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
import axios from 'axios';


export default ({
  name: 'Search',
  data(){
    return{        
      numberToConvert: '',
      dataArray: [],
      selected: '',
      
    }
  },
  emits: ['selectMoney', 'selectedSearch', 'numberSearch'],
  methods: {
   toResult(){
     if(this.numberToConvert > 0 && this.selected){
            this.$emit('selectedSearch', this.selected);
            this.$emit('numberSearch', this.numberToConvert);
     }

   }
  },
  components: {
    IonRouterOutlet,
    IonInput,
    IonLabel,
    IonItem,
    IonSelect,
    IonSelectOption,
  },
  mounted(){
    axios
        .get(`http://data.fixer.io/api/latest?access_key=${process.env.VUE_APP_API_KEY}`)
        .then((response) =>{
            console.log(response.data.rates);
             this.dataArray = Object.keys(response.data.rates).map(function(value) {
              return [value, response.data.rates[value]];
            })
            this.$emit('selectMoney', this.dataArray);
          
        })
        .catch((error) => {
          console.log(error);
        })
  }

});
</script>