<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} and {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import * as EventService from "@/services/EventServices";
export default defineComponent({
  name: "EventDetailsView",
  props: ["id"],
  data() {
    return { event: null };
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => (this.event = response.data))
      .catch((err) => console.log(err));
  },
});
</script>
