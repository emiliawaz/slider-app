<template>
  <div class="c-slide">
    <img class="c-slide__image" :src="slide.image.url" />
    <Overlay 
      :title="slide.title" 
      :text="slide.text" 
      :buttons="slide.buttons" />
  </div>
</template>

<script>
import Overlay from "./Overlay.vue";

export default {
  name: "Slide",

  components: {
    Overlay,
  },

  props: {
    slide: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style lang="scss">
.c-slide {
  position: relative;
}

.c-slide__image {
  display: block;
  max-width: 100%;
}
</style>
