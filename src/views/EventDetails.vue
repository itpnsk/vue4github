<template>
  <div>
    <h1 v-if="event.title != null">{{ event.title }}</h1>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'

export default {
  props: {
    id: {
      type: Number
    }
  },
  data() {
    return {
      event: {},
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then(response => {
        this.event = response.data
        console.log(this.event)
      })
      .catch(error => {
        console.log(error)
      })
  }
}
</script>
