<template>
  <div class="card">
    <header class="card-header">
      <p class="card-title card-header-title is-centered is-quarter">{{ cardTitle }}</p>
    </header>
    <div class="card-image">
      <figure class="image is-5by3">
        <img :src="cardImageUrl" alt="card image">
      </figure>
    </div>
    <div class="card-content">{{ cardDescription }}</div>
  </div>
</template>

<script>
// import * as R from "ramda";
import { pathOr } from "ramda";

export default {
  props: {
    card: Object
  },
  methods: {
    getValueFromCard(initValue, path) {
      const ramdaFunction = pathOr(initValue, path);
      // will return a default value even if the card is null
      return ramdaFunction(this.card);
    }
  },
  computed: {
    cardImageUrl() {
      const defaultUrl = "https://via.placeholder.com/150";
      return this.getValueFromCard(defaultUrl, ["imageUrl"]);
    },
    cardTitle() {
      const defaultTitle = "Title";
      return this.getValueFromCard(defaultTitle, ["title"]);
    },
    cardDescription() {
      const defaultDescription = "Card description";
      return this.getValueFromCard(defaultDescription, ["description"]);
    }
  }
};
</script>

<style scoped>
.card-title {
  overflow-x: hidden;
  white-space: nowrap;
}

.card {
  width: 200px;
  height: 300px;
  margin: 15px;
  flex: 0 0 auto;
  overflow-y: hidden;
}

.card-content {
  height: 110px;
  overflow-y: hidden;
}
.card-content:after {
  content: "";
  position: absolute;
  z-index: 1;
  bottom: 0;
  left: 0;
  background-image: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 0),
    rgba(255, 255, 255, 1) 90%
  );
  width: 100%;
  height: 4em;
}
</style>
