<template>
  <q-page class="flex flex-center">
    <div style="height: 90vh;">
      <div class="fit" id="meet"></div>
    </div>
    <div style="margin: auto;" v-if="!meetCall" >
      <div class="row" style="width: 40vw;margin: auto;">
        <img src="https://i0.wp.com/fatiherikci.com/wp-content/uploads/2020/03/jitsimeet.jpg?fit=1038%2C570&ssl=1" class="fit">        
      </div>
      <div class="row justify-center">
        <input v-model ="meetName" placeholder="Set your meeting name"  type="text">
        <button @click="intomeet" >Create Jitsi Meeting</button>            
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useRouter, useRoute } from 'vue-router'

//https://meet.jit.si/test123
export default defineComponent({
  name: 'IndexPage',
  setup () {
    const router = useRouter();
    const meetName = ref(null);
    const meetCall = ref(null);

    const intomeet = () => {
      const domain = 'meet.jit.si';
      const options = {
          roomName: 'JitsiMeetAPIExample',
          width: 1200,
          height: 600,
          parentNode: document.querySelector('#meet'),
          lang: 'en'
      };
      const api = new JitsiMeetExternalAPI(domain, options);
      meetCall.value = true;
    }

    return {
      router,
      intomeet,
      meetCall,
    }
  }
})
</script>
