<template>
  <div class="row">
    <div class="col">
      <img :src="albums.poster" :alt="albums.author" />
      <h3>{{ albums.title }}</h3>
      <p>{{ albums.author }}</p>
      <p>{{ albums.year }}</p>
    </div>
  </div>
</template>

<script>
// esempio crad presa da API
/*
  author: "Bon Jovi"
  genre: "Rock"
  poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
  title: "New Jersey"
  year: "1988"
*/

import axios from "axios";

export default {
  name: "DiscItemComponent",
  data() {
    return {
      albums: [],
    };
  },
  mounted() {
    this.cardsDisc();
  },
  methods: {
    cardsDisc() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.albums.push(response.data);
          console.log(this.albums);
        });
    },
  },
};
</script>

<style scoped lang="scss">
</style>