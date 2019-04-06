<template>
  <div id="app">
    <CardList :cards="cards"/>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./modules/models/card";

export default {
  name: "app",
  data() {
    return {
      cards: [], //new Array(6).fill({}, 0, 6),
      api:
        "https://my-json-server.typicode.com/bigriceeater/food-restaurant-data/restaurants"
    };
  },
  components: {
    CardList: require("@/components/card-list").default
  },
  created() {
    axios.get(this.api).then(res => {
      res.data.forEach(restaurant => {
        const card = new Card({
          title: restaurant.title,
          imageUrl: restaurant.imageUrl,
          description: restaurant.description
        });
        this.cards.push(card);
      });
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
