<template>
  <div>
    <h2>List Blog</h2>
    <list-blog :dataBlog="dataBlog" />
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "list-blog-component",
  data() {
    return {
      dataBlog: [],
    };
  },
  mounted() {
    this.fetch();
  },

  methods: {
    fetch() {
      axios.get("http://localhost:3001/blogs").then((res) => {
        this.dataBlog = res.data;
      });
    },
  },
};
</script>
<style>
h2 {
  margin-bottom: 20px;
}
</style>