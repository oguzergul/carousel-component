<template>
  <div class="carousel" @keydown="checkSlide($event)" tabindex="0">
    <slot></slot>
    <button @click.prevent="next" class="btn btn-next">
      <IconArrowRight/>
    </button>
    <button @click.prevent="prev" class="btn btn-prev">
      <IconArrowLeft/>
    </button>
  </div>
</template>
<script>
import IconArrowLeft from '../assets/icons/left-arrow.svg'
import IconArrowRight from '../assets/icons/right-arrow.svg'

export default {
  components: {
    IconArrowLeft,
    IconArrowRight
  },
  data() {
    return {
      index: 0,
      slides: [],
      slideDirection: '',
    }
  },
  computed: {
    slidesLength() {
      return this.slides.length;
    }
  },
  mounted() {
    this.slides = this.$children;
    this.slides.map((slide, index) => {
      slide.index = index;
    });
  },
  methods: {
    next() {
      this.index++;
      if (this.index >= this.slidesLength) {
        this.index = 0;
      }
      this.slideDirection = 'slide-right';
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.slidesLength - 1;
      }
      this.slideDirection = 'slide-left';
    },
    checkSlide(event) {
      if (event.keyCode === 39) {
        this.next();
      } else if (event.keyCode === 37) {
        this.prev();
      } else return
    },
  }
}
</script>