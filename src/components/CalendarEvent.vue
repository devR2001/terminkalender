<template>
  <div id="calendar-event">
    <div class="alert text-center">
      <div>
        <strong>{{ event.priority }}</strong>
      </div>

      <div>{{ event.title }}</div>

      <div>
        <i class="fas fa-edit me-2" role="button"></i>
        <i class="far fa-trash-alt" role="button"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "CalendarEvent",
    props: {
      event: Object,
    },
};
</script>

<style scoped></style>
