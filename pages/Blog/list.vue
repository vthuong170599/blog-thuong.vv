<template>
  <div>
    <list-blog :dataBlog="dataBlog" @getDataBlogAfterDelete="fetch"/>
  </div>
</template>

<script>
import ListBlog from "../../components/blog/ListBlog";
import axios from "axios";
export default {
  components: {
    ListBlog,
  },
  data() {
    return {
      dataBlog: [],
    };
  },
  mounted() {
    this.fetch();
  },
  methods: {
    /** get data of blog api
     * @since 18-3-2021
     */
    fetch() {
      axios.get("http://localhost:3001/blogs").then((res) => {
        this.dataBlog = res.data;
      });
    },
  },
};
</script>

<style scope>
</style>
