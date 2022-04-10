<template>
  <div class="container-cd">
    <div class="--dg-card text-center">
      <img class="pt-3 pb-2" :src="album.poster" alt="album.title" />
      <h2 class="mt-2">{{ album.title }}</h2>
      <p class="mt-2">{{ album.author }}</p>
      <p class="pb-3 --dg-year">{{ album.year }}</p>
    </div>
  </div>
</template>

<script>
// esempio card presa da API
/*
  author: "Bon Jovi"
  genre: "Rock"
  poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
  title: "New Jersey"
  year: "1988"
*/
export default {
  name: "DiscItemComponent",
  props: {
    album: Object,
  },
};
</script>

<style scoped lang="scss">
@import "@/style/varstyle";
.container-cd {
  width: calc(100% / 5);
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
  .--dg-card {
    background-color: $overlay-color;
    width: 130px;
    height: 240px;

    img {
      width: 100px;
    }

    h2 {
      color: $title-white;
      font-size: $f-size-9;
      font-weight: $text-bold;
      text-transform: $text-upper;
    }

    p {
      font-size: $f-size-9;
      margin-bottom: 0;
      line-height: 18px;
      color: $subtitle-lightgray;
    }

    .--dg-year {
      font-size: $f-size-7;
    }
  }
}
</style>