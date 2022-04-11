<template>
  <div class="row">
    <div class="col p-3">
      <span class="me-2">Seleziona il tuo genere preferito</span>
      <select @change="filteredGenre" name="select" id="genres-select">
        <option value="All">All</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectComponent",

  data() {
    return {
      genre: "",
    };
  },
  methods: {
    filteredGenre(event) {
      //   console.log(event.target.value);
      this.genre = event.target.value;
      this.$emit("changeGenre", this.genre);
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/style/varstyle";

span {
  color: $title-white;
  text-transform: $text-upper;
  font-size: $f-size-8;
}

#genres-select {
  font-size: $f-size-8;
  border-radius: 10px;
  padding: 3px 5px;
  color: $title-white;
  background-color: $overlay-color;
  &:focus-visible {
    outline: 2px solid #1ed760;
  }
}
</style>