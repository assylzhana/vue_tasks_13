<template>
  <div class="custom-timeline">


    <div v-for="event in sortedEvents" :key="event.date" class="custom-event">
      <div class="event-info">

        <h3>
          {{ event.title }}
        </h3>
        <p class="event-date">
          {{ formattedDate(event.date) }}
        </p>
        <p class="event-description">
          {{ event.description }}
        </p>
      </div>
    </div>
    

  </div>
</template>

<script>
export default {
  props: {
    events: Array,
  },
  computed: {
    sortedEvents() {
      return this.events.sort((a, b) => new Date(a.date) - new Date(b.date));
    },
  },
  methods: {
    formattedDate(dateString) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      return new Date(dateString).toLocaleDateString(undefined, options);
    },
  },
};
</script>

<style scoped>
.custom-timeline {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.custom-event {
  border: 1px solid #ddd;
  padding: 20px;
  margin: 15px 0;
  border-radius: 8px;
  background-color: #f5f5f5;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.event-info {
  text-align: left;
}

.event-date {
  font-weight: bold;
  color: #555;
  margin-bottom: 8px;
}

.event-description {
  color: #333;
}
</style>
