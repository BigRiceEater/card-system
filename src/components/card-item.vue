<template>
  <div class="card">
    <div class="card-header">
      <p class="card-header-title is-centered">{{ cardTitle }}</p>
    </div>

    <div class="card-image">
      <figure class="image is-4by3">
        <img :src="cardImageUrl" alt="card image">
      </figure>
    </div>

    <div class="card-content">
      <p>{{ cardDescription }}</p>
    </div>
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
.card {
  width: 200px;
  margin: 5px;
}
.card-content {
  min-height: 125px;
  max-height: 125px;
  overflow: hidden;
}

img {
  object-fit: cover;
}

/* Fade the bottom text if too much
.card-content:before {
  content: "";
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  background: linear-gradient(transparent 50px, black);
} */
</style>
