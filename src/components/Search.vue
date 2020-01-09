<template>
  <div>
    <div class="container">
      <input class="text" type="text" v-model="term" @keyup.enter="exe" />
      <input class="submit" type="submit" value="Search" @click="exe" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      term: ""
    };
  },
  methods: {
    async exe() {
      this.$emit("loadStart");
      const { data } = await axios.get(
        `//itunes.apple.com/search?term=${this.term}&country=jp&entity=musicVideo`
      );
      this.$emit("loadComplete", { results: data.results });
    }
  }
};
</script>
