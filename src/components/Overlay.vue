<template>
  <div class="c-overlay">
    <h1 class="c-overlay__title">{{ title }}</h1>
    <p class="c-overlay__text">{{ text }}</p>
    <div class="c-overlay__buttons">
      <a
        class="c-overlay__button"
        v-for="button in buttons"
        :key="button.id"
        :href="button.url"
      >
        {{ button.text }}
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Overlay",

  props: {
    title: {
      type: String,
      default: "",
    },
    text: {
      type: String,
      default: "",
    },
    buttons: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss">
.c-overlay {
  position: absolute;
  color: #fff;
  text-align: center;
  top: 50%;
  transform: translateY(-50%);
  left: 0;
  right: 0;
  margin: 0 1rem;
  font-size: 0.6rem;

  @media (min-width: 479px) {
    font-size: 1rem;
    margin: 0 6.5rem;
  }
}

.c-overlay__title {
  text-transform: uppercase;
}

.c-overlay__text::first-letter {
  text-transform: uppercase;
}

.c-overlay__button {
  display: inline-block;
  text-decoration: none;
  color: #fff;
  border: 2px solid #fff;
  text-transform: uppercase;
  font-weight: bold;
  padding: 0.6rem 2.5rem;
  margin: 0.5rem;
  font-size: 0.8rem;
  width: calc(100% - 6rem);

  @media (min-width: 479px) {
    margin: 1rem;
    width: auto;
  }
}
</style>
