<template>
  <div class="card border-start" :class="cardClasses">
    <div
      class="card-header text-center"
      role="button"
      :class="cardHeaderClasses"
    >
      <strong>{{ day.fullName }}</strong>
    </div>
    <div class="card-body">
      <CalendarEvent
        v-for="event in day.events"
        :key="event.title"
        :event="event"
      >
        <template v-slot:eventPriority="slotProps"
          ><h5>{{ slotProps.priorityDisplayName }}</h5></template
        >
        <!-- <template v-slot:default></template> -->
        <template v-slot:event="slotProps"><i>{{ slotProps.event.title }}</i></template>
      </CalendarEvent>
    </div>
  </div>
</template>

<script>
import CalendarEvent from "./CalendarEvent.vue";
import Store from "@/store";

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
    day: {
      type: Object,
      required: true,
      // Bei primitiven Datentypen: default: 100
      // Bei nicht-primitiven Datentypen
      default: function () {
        // Wenn keine Daten vorhanden sind, dann wird dieser Teil ausgegeben
        return {
          id: -1,
          fullName: "Fehlender Wochentag",
          events: [],
        };
      },
      // value ist in dem Fall dann "day"
      validator: function (value) {
        if (Object.keys(value).includes("id")) {
          return true;
        }
      },
    },
  },
  computed: {
    cardClasses() {
      return this.day.id === Store.getters.activeDay().id
        ? ["border-primary"]
        : null;
    },
    cardHeaderClasses() {
      return this.day.id === Store.getters.activeDay().id
        ? ["bg-primary", "text-white"]
        : null;
    },
  },
};
</script>

<style scoped></style>
