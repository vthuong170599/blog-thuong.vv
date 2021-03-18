<template>
  <div>
    <h2>Search Blogs</h2>
    <search-form @SendDataBlog="GetDataBlog" />
    <List-blog :dataBlog="listBlog" />
  </div>
</template>

<script>
export default {
   data(){
    return {
      listBlog: []
    }
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

<style scope>
form {
  margin-top: 3%;
}
</style>
