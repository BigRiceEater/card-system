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
import * as R from "ramda";

export default {
  props: {
    card: Object
  },
  methods: {
    getValueFromCard(initValue, path) {
      const ramdaFunction = R.pathOr(initValue, path);
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
}
</style>
