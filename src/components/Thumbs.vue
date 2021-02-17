<template>
  <div class="c-thumbs">
    <ul class="c-thumbs__list">
      <li
        class="c-thumbs__element"
        v-for="index in length"
        :key="`index-${index}`"
      >
        <span
          class="c-thumbs__circle"
          :class="currentIndex + 1 === index ? 'c-thumbs__circle--active' : ''"
          @click="$emit('change-slide', index - 1)"
          @keyup.enter="$emit('change-slide', index - 1)"
          tabindex="0"
        ></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Thumbs",

  props: {
    length: {
      type: Number,
      default: 0,
    },
    currentIndex: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style lang="scss">
.c-thumbs {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  margin-bottom: 2rem;
}

.c-thumbs__list {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.c-thumbs__element {
  display: inline-block;
  cursor: pointer;
  margin: 0.5rem;
}

.c-thumbs__circle {
  display: block;
  background: #fff;
  width: 0.5rem;
  height: 0.5rem;
  border-radius: 50%;

  &.c-thumbs__circle--active {
    opacity: 0.5;
  }
}
</style>
