<template>
  <div>
    <h2>Search Blogs</h2>
    <search-form  @SendDataBlog="GetDataBlog"/>
    <h2 class="mt-5">Search Blog</h2>
    <List-blog :dataBlog="listBlog" />
  </div>
</template>
<script>
import ListBlog from "../ListBlog";
import SearchForm from '../SearchForm';
export default {
  name: "search-component",
  // props: {
  //   listBlog: {
  //     type: Array,
  //     default: ()=>[]
  //   }
  // },
  data(){
    return {
      listBlog: []
    }
  },
  components: {
    ListBlog,
    SearchForm
  },
  methods: {
     /** Get blog by emit in searchForm component
     * @since 18-3-2021
     */
    GetDataBlog(Data){
      this.listBlog = Data;
    }
  }
};
</script>