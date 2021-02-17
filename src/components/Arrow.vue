<template>
  <div class="c-arrow">
    <button
      class="c-arrow__button"
      :aria-label="isLeft ? 'Previous slide' : 'Next slide'"
      @click="$emit('change-slide')"
    >
      <span
        class="c-arrow__symbol"
        :class="isLeft ? '' : 'c-arrow__symbol--right'"
      ></span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Arrow",

  props: {
    isLeft: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

<style lang="scss">
.c-arrow__button {
  cursor: pointer;
  background: transparent;
  border: 0;
  margin: 2rem;
}

.c-arrow__symbol {
  display: inline-block;
  border: solid #fff;
  border-width: 0 1px 1px 0;
  width: 1.5rem;
  height: 1.5rem;
  transform: rotate(135deg);

  &.c-arrow__symbol--right {
    transform: rotate(-45deg);
  }
}
</style>