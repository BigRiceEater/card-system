<template>
  <div class="card-list">
    <div class="inner">
      <div class="wrapper">
        <span class="more-arrow">></span>
        <Card
          v-for="(card,index) in cards"
          :card="card"
          :key="index"
          :isLastCard="index === cards.length-1"
        />
      </div>
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

/* Just for scrolling */
.card-list {
  overflow-x: auto;
  padding: 30px;
}

/* Need this in order to respect padding in .card-list*/
.inner {
  display: inline-block;
}

/* This is where we actually horizontally stack our items*/
.wrapper {
  display: flex;
  align-items: center;
  flex-wrap: nowrap;
}
</style>

