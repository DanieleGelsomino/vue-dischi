<template>
  <div class="--dg-container-albums d-flex justify-content-center">
    <div
      class="d-flex justify-content-center flex-wrap"
      v-if="albums.length > 0"
    >
      <DiscItem v-for="(song, index) in albums" :key="index" :album="song" />
    </div>
    <div v-else class="loading-file">
      <Loading />
    </div>
  </div>
</template>

<script>
import DiscItem from "@/components/DiscItem.vue";
import Loading from "@/components/Loading.vue";
import axios from "axios";

export default {
  name: "MainComponent",
  components: {
    DiscItem,
    Loading,
  },
  data() {
    return {
      albums: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.albums = response.data.response;
        console.log(this.albums[0]);
      });
  },
};
</script>

<style scoped lang="scss">
@import "@/style/varstyle";

.--dg-container-albums {
  flex-wrap: wrap;
  width: 63%;
  margin: 50px auto;
  padding: 55px;
}
</style>