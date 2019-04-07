<template>
  <div class="card-list">
    <div class="inner-wrapper">
      <span class="more-arrow">></span>
      <Card
        v-for="(card,index) in cards"
        :card="card"
        :key="index"
        :isLastCard="index === cards.length-1"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cards: Array
  },
  components: {
    Card: require("@/components/card-item").default
  }
};
</script>

<style scoped>
.more-arrow {
  font-size: 3em;
  margin: 20px;
}

.card-list {
  overflow-x: auto;
  padding: 30px;
}

.inner-wrapper {
  display: flex;
  align-items: center;
  flex-wrap: nowrap;
}
</style>

