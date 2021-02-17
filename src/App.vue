<template>
  <div id="app">
    <Slider :content="content" />
  </div>
</template>

<script>
import axios from "axios";
import Slider from "./components/Slider.vue";

export default {
  name: "App",

  components: {
    Slider,
  },

  data() {
    return {
      content: [],
    };
  },

  mounted() {
    axios
      .get("http://jsonplaceholder.typicode.com/photos?_start=0&_limit=4")
      .then((response) => {
        this.content = response.data.map((image) => {
          let newElement = {};

          newElement.title = image.title;
          newElement.text = image.title;
          newElement.buttons = [
            { text: "Button 1", url: image.url },
            { text: "Button 2", url: image.url },
          ];
          newElement.image = {
            id: image.id,
            url: image.url,
          };

          return newElement;
        });
      });
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 15px;
}
</style>
