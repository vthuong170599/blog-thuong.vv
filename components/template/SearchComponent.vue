<template>
    <div>
        <h2>Search Blogs</h2>
    <div>
      <div class="form-group">
        <div class="row">
          <div class="col-2">
            <label for="title">Tiêu đề</label>
          </div>
          <div class="col-10">
            <input
              type="text"
              name=""
              id="title"
              class="form-control"
              placeholder="Tiêu đề"
              aria-describedby="helpId"
              v-model="Search"
            />
          </div>
        </div>
      </div>
      <button  class="btn btn-success" @click="searchBlog()">Search</button>
    </div>
    <h2 class="mt-5">{{ titleTable }}</h2>
    <List-blog :dataBlog="listBlog" />
    </div>
</template>
<script>
import axios from "axios";
import ListBlog from '../ListBlog';
export default {
    name: 'search-component',
     props: {},
  data() {
    return {
      titlePage: "Search Blogs",
      titleTable: "List Blogs",
      Search: "",
      listBlog: [],
    };
  },
  methods: {
    // fucntion search blog
    searchBlog() {
      axios.get("http://localhost:3001/blogs" +"?title_like=" +this.Search).then((res) => {
        this.listBlog = res.data;
        console.log(res.data);
      });
    },
  },
  components: {
    ListBlog
  }
}
</script>