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
      <button  class="btn btn-success" @click="search()">Search</button>
    </div>
    <h2 class="mt-5">{{ titleTable }}</h2>
    <List-blog :dataBlog="listBlog" />
    </div>
</template>
<script>
import axios from "axios";
export default {
    name: 'search-component',
     props: {},
  data() {
    return {
      titlePage: "Search Blogs",
      titleTable: "List Blogs",
      Search: "",
      listBlog: [],

      // listBlogFilter: [],
    };
  },
  mounted() {
    // this.search();
  },
  computed: {
    // listBlogFilter: function () {
    //   return this.listBlog.filter((blog) => blog.title.includes(this.search));
    // },
  },
  methods: {
    search() {
      // const url = "http://localhost:3001/blogs?title=" + this.Search;
      axios.get("http://localhost:3001/blogs" +"?title_like=" +this.Search).then((res) => {
        this.listBlog = res.data;
        console.log(res.data);
      });
    },
  },
}
</script>