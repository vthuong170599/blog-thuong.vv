<template>
  <div>
    <h2>{{ title }}</h2>
    <List-blog :dataBlog="dataBlog"/>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      title: "List Blog",
      dataBlog: [],
    };
  },
    mounted() {
    this.fetch();
    // console.log(this.dataBlog)
  },

  methods: {
    Edit() {
      this.$router.push("/edit");
    },

    fetch() {
      axios
        .get("http://localhost:3001/blogs")
        .then((res) => (this.dataBlog = res.data));
        // console.log(this.dataBlog);
    },
  },
};
</script>

<style scope>

</style>
