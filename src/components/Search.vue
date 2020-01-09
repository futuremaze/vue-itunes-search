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
