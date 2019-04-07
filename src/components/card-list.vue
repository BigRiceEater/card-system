<template>
  <div class="card-list">
    <Card v-for="(card,index) in cards" :card="card" :key="index"/>
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
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
}
</style>

