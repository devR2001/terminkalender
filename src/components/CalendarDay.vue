<template>
  <div class="card" >
    <div class="card-header text-center" role="button">
      <strong>{{ day.fullName }}</strong>
    </div>
    <div class="card-body">
      <CalendarEvent />
    </div>
  </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";

export default {
  name: "CalendarDay",
  components: {
    CalendarEvent,
  },
  // Array Schreibweise; Nicht zu empfehlen
  // props: ["day"]

  // Objekt-Schreibweise
  props: {
    // Mögliche Typen: String, Number, Boolean, Object, Array oder Function
    // Mehrere Typen mit Array-Schreibweise: [String, Number]
    day: Object
  }
};
</script>

<style scoped></style>
