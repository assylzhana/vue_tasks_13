<template>
  <div id="app">
    <Timeline :events="eventsData" />

    <Accordion :accordionItems="accordionItems">
      <template v-slot:content="{ item }">
        <div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.description }}</p>
        </div>
      </template>
    </Accordion>

    <Carousel>
      <Slide v-for="slide in carouselItems" :key="slide.id">
        <div class="carousel__item">
          <img :src="slide.src" :alt="slide.alt" />
          <div class="carousel__caption">{{ slide.caption }}</div>
        </div>
      </Slide>

      <template #addons>
        <Navigation />
        <Pagination />
      </template>
    </Carousel>
  </div>
</template>

<script>
import Timeline from "./components/Timeline.vue";
import Accordion from "./components/Accordion.vue";
import { defineComponent } from "vue";
import { Carousel, Navigation, Pagination, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  components: {
    Timeline,
    Accordion,
    Carousel,
    Slide,
    Navigation,
    Pagination,
  },
  data() {
    return {
      eventsData: [
        {
          title: "Some data",
          date: "2023-01-15",
          description: "description to event",
        },
        {
          title: "Some data",
          date: "2023-02-28",
          description: "description to event",
        },
        {
          title: "Some data",
          date: "2023-04-10",
          description: "description to event",
        },
      ],
      accordionItems: [
        { name: "about", title: "About Us" },
        { name: "services", title: "Our Services" },
        { name: "contact", title: "Contact Us" },
      ],
      carouselItems: [
        {
          id: "1",
          src: "vue_tasks_13\src\assets\image1.webp",
          alt: "Nature Image 1",
          caption: "Explore the beauty of nature.",
        },
        {
          id: "2",
          src: "vue_tasks_13\src\assets\image2.jpg",
          alt: "Nature Image 2",
          caption: "Discover new landscapes and adventures.",
        },
        {
          id: "3",
          src: "vue_tasks_13\src\assets\image3.jpg",
          alt: "Nature Image 3",
          caption: "Connect with the serenity of the outdoors.",
        },
      ],
    };
  },
});
</script>

<style>
#app {
  font-family: "Arial", sans-serif;
  text-align: center;
  color: #333;
  padding: 20px;
}

.carousel__item {
  min-height: 300px;
  width: 100%;
  background-color: #f0f0f0;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.carousel__caption {
  margin-top: 10px;
  font-size: 18px;
  color: #555;
}

</style>
