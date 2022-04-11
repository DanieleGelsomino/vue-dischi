<template>
  <div
    class="--dg-container-albums d-flex justify-content-center container-fluid"
  >
    <Select @changeGenre="genreSelect" />
    <div
      class="d-flex justify-content-center flex-wrap"
      v-if="albums.length > 0"
    >
      <DiscItem
        v-for="(song, index) in filterGenre"
        :key="index"
        :album="song"
      />
    </div>
    <div v-else class="loading-circle">
      <Loading />
    </div>
  </div>
</template>

<script>
import DiscItem from "@/components/DiscItem.vue";
import Loading from "@/components/Loading.vue";
import axios from "axios";
import Select from "@/components/Select.vue";

export default {
  name: "MainComponent",
  components: {
    DiscItem,
    Loading,
    Select,
  },
  data() {
    return {
      albums: [],
      genres: "",
    };
  },

  mounted() {
    this.loadAlbums();
  },

  computed: {
    filterGenre() {
      if (this.genres === "All") {
        return this.albums;
      }
      const filteredGenre = this.albums.filter((song) => {
        return song.genre.includes(this.genres);
      });
      return filteredGenre;
    },
  },

  methods: {
    loadAlbums() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          if (response.status === 200) {
            this.albums = response.data.response;
            //console.log(this.albums[0]);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    genreSelect(genres) {
      this.genres = genres;
    },
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

  .loading-circle {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(50% - 50%);
  }
}

@media screen and (min-width: 700px) {
  .--dg-container-albums {
    width: 100%;
  }
}

@media screen and (min-width: 900px) {
  .--dg-container-albums {
    width: 85%;
  }
}

@media screen and (min-width: 1000px) {
  .--dg-container-albums {
    width: 75%;
  }
}

@media screen and (min-width: 1235px) {
  .--dg-container-albums {
    width: 65%;
  }
}

@media screen and (min-width: 1500px) {
  .--dg-container-albums {
    width: 65%;
  }
}
</style>