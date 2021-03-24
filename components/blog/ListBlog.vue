<template>
  <div>
    <h2>List Blog</h2>
    <table class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Tin</th>
          <th>Loại</th>
          <th>Trạng thái</th>
          <th>Vị trí</th>
          <th>Ngày public</th>
          <th>Edit</th>
          <th>Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(blog, index) in dataBlog" :key="index">
          <td scope="row">{{ index + 1 }}</td>
          <td>{{ blog.title }}</td>
          <td>{{ findCategory(blog.category) }}</td>
          <td>{{ blog.public == true ? "yes" : "no" }}</td>
          <td>{{ filterPosition(blog.position) }}</td>
          <!-- <td>{{ blog.position }}</td> -->
          <td>{{ blog.data_pubblic }}</td>
          <td>
            <nuxt-link class="btn btn-outline-success" :to="`/Blog/${blog.id}`"
              >edit</nuxt-link
            >
          </td>
          <td>
            <button class="btn btn-outline-danger" @click="DeleteBlog(blog.id)">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from "axios";
import { CATEGORY } from "../../constant/constant";
import { POSITION } from "../../constant/constant";
import swal from "sweetalert2";
export default {
  name: "list-blog",
  props: {
    dataBlog: {
      type: Array,
      default: () => [],
    },

  },
  data() {
    return {
      CATEGORY: CATEGORY,
      POSITION: POSITION,
      number: [],
    };
  },
  
  mounted(){

  },

  methods: {
    /** delete Blog by id
     * send dataBlog to the list Page
     * @param  id id for element Blog
     *
     * @since 18-3-2021
     */
    DeleteBlog(id) {
      swal
        .fire({
          title: "Are you sure?",
          text: "You won't be able to revert this!",
          icon: "warning",
          showCancelButton: true,
          confirmButtonColor: "#3085d6",
          cancelButtonColor: "#d33",
          confirmButtonText: "Yes, delete it!",
        })
        .then((result) => {
          if (result.isConfirmed) {
            axios.delete("http://localhost:8000/api/blog/" + id).then((res) => {
              this.$emit("getDataBlogAfterDelete", this.dataBlog);
            });
            swal.fire("Deleted!", "Your file has been deleted.", "success");
          }
        });
    },

    /** find Blog by id category = key CATEGORY
     * @param  id id for blog.category
     *
     * @since 18-3-2021
     */
    findCategory(id) {
      return this.CATEGORY.find((cate, index) => {
        if (index === id) {
          return cate;
        }
      });
    },

    /** find Blog by id position = key POSITION
     * @param  id id for blog.position
     *
     * @since 18-3-2021
     */
    filterPosition(pos) {
      return pos
        .map((item) => {
          return this.POSITION[item];
        })
        .join(",");
    },
  },
};
</script>
<style scoped>
</style>