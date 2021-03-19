<template>
  <div>
    <h2>Search Blogs</h2>
    <search-form @sendKeyWord="searchBlog"/>
    <list-blog :dataBlog="listBlog"/>
  </div>
</template>

<script>
import axios from "axios";
import SearchForm from '../../components/blog/SearchForm';
import ListBlog from '../../components/blog/ListBlog';
export default {
  components: {
    SearchForm,
    ListBlog
  },
   data(){
    return {
      listBlog: []
    }
  },
  methods: {
    /** search data of blog by key word
     * @since 18-3-2021
     */
    searchBlog(data) {
      axios
        .get("http://localhost:3001/blogs?title_like=" + data )
        .then((res) => {
          this.listBlog = res.data;
        });
    },

  },
  // updated(){
  //   console.log('sdas');
  // }
};
</script>

<style scope>
form {
  margin-top: 3%;
}
</style>
