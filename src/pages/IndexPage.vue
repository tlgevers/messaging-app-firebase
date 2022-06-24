<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md row justify-center">
        <MessageBox 
          v-for="message in messages" 
          v-bind="message" 
          :key="message.id"
        />
        <q-input 
          style="width: 100%" 
          outlined 
          v-model="inputtext" 
          label="Message" 
          @keyup.enter="captureInput" 
        />
    </div>

    <!-- <img -->
    <!--   alt="Quasar logo" -->
    <!--   src="~assets/quasar-logo-vertical.svg" -->
    <!--   style="width: 200px; height: 200px" -->
    <!-- > -->
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import MessageBox from 'components/MessageBox.vue'

let outmessage = []
let messages = [{
      id:"1", 
      message:["incoming"],
      sent: false
    },
    {
      id: "2",
      message:["outgoing"]
    }]

let inputtext = ref('')
export default defineComponent({
  name: 'IndexPage',
  methods: {
    captureInput: (e) => {
        console.log(inputtext.value)
        console.log(messages.length+1)
        messages.push({id: messages.length+1, message: [inputtext.value], sent:true})
        inputtext.value = ''
    }
  },
  setup() {
    return {
        inputtext
    }
  },
  data() {
    return {
        messages: messages,
    } 
  },
  components: {
    MessageBox
  }
})
</script>
