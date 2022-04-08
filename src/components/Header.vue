<template>
  <div class="row icon-bar">
    <div class="col-12">
      <img class="" src="@/assets/spotify-logo.png" alt="logo-spotify" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style scoped lang="scss">
@import "@/style/varstyle";

.icon-bar {
  background-color: $overlay-color;
  img {
    width: 45px;
    margin-left: 5px;
    padding: 5px;
  }
}
</style>