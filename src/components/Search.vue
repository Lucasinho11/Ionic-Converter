<template>
    <ion-router-outlet />
    <ion-input type="number" value="333"></ion-input>
    <form>

    </form>
</template>

<script>

import { IonRouterOutlet, IonInput } from '@ionic/vue';



export default ({
  name: 'Form',
  data(){
    return{
      city: '',
        
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