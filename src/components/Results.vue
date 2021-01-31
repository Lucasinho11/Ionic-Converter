<template>
  <ion-router-outlet />
    <p>{{ this.result }}</p>

</template>
<style>

</style>
<script>

import {IonRouterOutlet} from '@ionic/vue';

export default ({
  name: 'Results',
  data(){
    return{        
        
      
    }
  },
  props : ['result'],
  emits:['convertMoney'],
  methods: {

       
  },
  components: {
    IonRouterOutlet,

  },

});

</script>