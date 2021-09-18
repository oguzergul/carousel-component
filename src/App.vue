<template>
  <div class="container">
    <h1>Vue Carousel Component</h1>
    <Carousel>
      <CarouselSlide v-for="(slide,index) in slides" :key="index" class="carousel-slider">
        <img :src="slide" :alt="slide">
      </CarouselSlide>
    </Carousel>
  </div>
</template>

<script>
import Carousel from './components/Carousel.vue';
import CarouselSlide from './components/Carouseltem';
import {IMAGES} from "./assets/images";

export default {
  data() {
    return {
      slides: IMAGES
    }
  },
  components: {
    Carousel,
    CarouselSlide,
  },
}
</script>
