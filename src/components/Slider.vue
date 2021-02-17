<template>
  <div class="c-slider">
    <transition-group class="c-slider__transition" name="fade" tag="div">
      <div class="c-slider__slides" v-for="i in [currentIndex]" :key="i">
        <Arrow
          class="c-slider__arrow c-slider__arrow--left"
          :isLeft="true"
          @change-slide="changeSlide(currentIndex - 1)"
        />
        <Slide v-if="content[currentIndex]" :slide="content[currentIndex]" />
        <Arrow
          class="c-slider__arrow c-slider__arrow--right"
          :isLeft="false"
          @change-slide="changeSlide(currentIndex + 1)"
        />
        <Thumbs
          class="c-slider__thumbs"
          :length="content.length"
          :currentIndex="currentIndex"
          @change-slide="changeSlide"
        />
      </div>
    </transition-group>
  </div>
</template>

<script>
import Arrow from "./Arrow.vue";
import Slide from "./Slide.vue";
import Thumbs from "./Thumbs.vue";

export default {
  name: "Slider",

  components: {
    Arrow,
    Slide,
    Thumbs,
  },

  props: {
    content: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    return {
      currentIndex: 0,
    };
  },

  mounted() {
    this.startSlider();
  },

  methods: {
    startSlider() {
      setInterval(() => {
        this.changeSlide(this.currentIndex + 1);
      }, 5000);
    },

    changeSlide(index) {
      let lastIndex = this.content.length - 1;

      this.currentIndex = index < 0 ? lastIndex : index > lastIndex ? 0 : index;
    },
  },
};
</script>

<style lang="scss">
.c-slider {
  text-align: center;
  position: relative;
}

.c-slider__transition {
  display: inline-block;
  overflow: hidden;

  .fade-enter-active,
  .fade-leave-active {
    display: block;
    transition: all 0.9s ease;
    overflow: hidden;
    visibility: visible;
    opacity: 1;
  }

  .fade-enter,
  .fade-leave-to {
    display: block;
    overflow: hidden;
    visibility: hidden;
    opacity: 0;
    position: absolute;
    top: 0;
  }
}

.c-slider__slides {
  position: relative;
  display: inline-block;
}

.c-slider__arrow {
  display: none;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1;

  &.c-slider__arrow--left {
    left: 0;
  }

  &.c-slider__arrow--right {
    right: 0;
  }

  @media (min-width: 479px) {
    display: block;
  }
}
</style>