<template>
  <div class="row justify-content-center">
    <div class="col-8 text-center">
      <DiscItem />
    </div>
  </div>
</template>

<script>
import DiscItem from "@/components/DiscItem.vue";

export default {
  name: "MainComponent",
  components: {
    DiscItem,
  },
};
</script>

<style scoped lang="scss">
</style>