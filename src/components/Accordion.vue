<template>
  <div class="custom-accordion">
    <div v-for="item in accordionItems" :key="item.name" class="accordion-item">


      <div class="accordion-header" @click="toggleAccordion(item)">


        <span class="accordion-title">{{ item.title }}</span>
        <span class="accordion-icon">{{ item.expanded ? '-' : '+' }}</span>
      </div>
      <div v-if="item.expanded" class="accordion-content">


        <slot name="content" :item="item"></slot>
      </div>

      
    </div>
  </div>
</template>

<script>
export default {
  props: {
    accordionItems: Array,
  },
  methods: {
    toggleAccordion(item) {
      item.expanded = !item.expanded;
    },
  },
};
</script>

<style scoped>
.custom-accordion {
  width: 100%;
}

.accordion-item {
  border: 1px solid #ddd;
  margin: 10px;
  border-radius: 8px;
  overflow: hidden;
  transition: border-color 0.3s ease-in-out;
}

.accordion-header {
  padding: 15px;
  background-color: #f4f4f4;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: background-color 0.3s ease-in-out;
}

.accordion-title {
  font-weight: bold;
}

.accordion-icon {
  font-size: 18px;
}

.accordion-content {
  padding: 15px;
  border-top: 1px solid #ddd;
}
</style>
