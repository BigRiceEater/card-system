<template>
  <div class="card-list">
    <div class="inner">
      <Card v-for="(card,index) in cards" :card="card" :key="index"/>
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
.card-list {
  padding: 25px;
  margin: 5px;
}
.inner {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  overflow: auto;
}
</style>

