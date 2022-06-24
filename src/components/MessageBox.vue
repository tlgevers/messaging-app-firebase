<template>
    <div style="width: 100%; max-width: 400px">
        <q-chat-message :text=message :sent=sent />
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MessageBox',
  props: {
    message: {
      type: Array,
      required: true
    },
    sent: {
      type: Boolean,
      default: true
    }
  }
})
</script>
