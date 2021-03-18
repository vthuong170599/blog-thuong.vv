<template>
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
    <button class="btn btn-success" @click="searchBlog()">Search</button>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      Search: "",
      DataBlog: [],
    };
  },
  methods: {
    /** search data of blog by key word
     * @since 18-3-2021
     */
    searchBlog() {
      axios
        .get("http://localhost:3001/blogs" + "?title_like=" + this.Search)
        .then((res) => {
          this.DataBlog = res.data;
          this.$emit("SendDataBlog", this.DataBlog);
        });
    },
  },
};
</script>