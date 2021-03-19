<template>
  <div>
    <h2>Search Blogs</h2>
    <search-form @sendKeyWord="searchBlog" />
    <list-blog
      :dataBlog="listBlog"
      @getDataBlogAfterDelete="getDataAfterSearch"
    />
  </div>
</template>

<script>
import axios from "axios";
import SearchForm from "../../components/blog/SearchForm";
import ListBlog from "../../components/blog/ListBlog";
export default {
  components: {
    SearchForm,
    ListBlog,
  },
  data() {
    return {
      Search: "",
      listBlog: [],
    };
  },
  methods: {
    /**
     * search data of blog by key word
     * @param {string} data - user list
     * @since 18-3-2021
     */
    searchBlog(data) {
      this.Search = data;
      const url = data ? 'http://localhost:3001/blogs?title_like=' + data : 'http://localhost:3001/blogs';
      axios
        .get(url)
        .then((res) => {
          this.listBlog = res.data;
        });
    },

    /** 
     * call back function searchBlog
     * @since 19-3-2021
     */
    getDataAfterSearch() {
      this.searchBlog(this.Search);
    },
  },
};
</script>

<style scope>
form {
  margin-top: 3%;
}
</style>
