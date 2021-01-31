<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>€uro Converter</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">€uro Converter</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <div id="container">
        <Search @selectMoney='dataArray' @selectedSearch='selectedSearch' @numberSearch='numberSearch'/>
        <Results v-if="result!= ''" :result='result'/>
        
      </div>
    </ion-content>
  </ion-page>
</template>
<script>
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import Search from '@/components/Search';
import Results from '@/components/Results';
export default {
  name: 'Home',
  data(){
    return{
      selectedMoney : '',
      amount: '',
      result: '',
    }
  },
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    Search,
    Results

  },
  
  methods: {
    convert(){
            this.result = (this.amount * this.selectedMoney).toFixed(2)
            console.log(this.selectedMoney)
            console.log(this.amount)
            console.log(this.result)
            return this.result;
       
    },
    dataArray(value) {
      console.log(value) // someValue
    },
    selectedSearch(value){
      this.selectedMoney = value,
      console.log(value)
    },
    numberSearch(value){
      this.amount = value,
      this.convert()
      console.log(value)
    },
  }
};
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>