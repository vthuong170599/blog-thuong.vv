<template>
  <div>
    <list-blog @getDataBlogAfterDelete="nextPage" :dataBlog="dataBlog"></list-blog>
    <!-- <nav aria-label="Page navigation">
      <ul class="pagination">
        <li class="page-item" v-for="(number, key) in page.links" :key="key">
          <a
            :class="'page-link' + number.active ? 'active' : ''"
            @click="nextPage(number.url)"
          >
            <span v-html="number.label"
          /></a>
        </li>
      </ul>
    </nav> -->

    <!-- <b-pagination-nav :pages="page.links" :number-of-pages="page.per_page" /> -->
    <b-pagination
      v-model="currentPage"
      :total-rows="page.total"
      :per-page="page.per_page"
      @page-click="nextPage"
      prev-text="Prev"
      next-text="Next"
    ></b-pagination>
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
      page: {},
      currentPage: 1,
    };
  },
  mounted() {
    this.nextPage();
  },
  methods: {
    /** get data of blog api
     * @since 18-3-2021
     */
    // fetch(page) {
    //   if (page == null) {
    //     page = 1;
    //   }
    //   axios.get("http://localhost:8000/api/blog?page=" + page).then((res) => {
    //     // console.log(res.data);
    //     this.dataBlog = res.data.data;
    //     this.page = res.data;
    //   });
    // },

    /** get data of blog api
     * @since 24-3-2021
     */
    nextPage(e, page) {
      axios.get("http://localhost:8000/api/blog?page=" + page).then((res) => {
        // console.log(res.data);
        this.dataBlog = res.data.data;
        this.page = res.data;
      });
    },
  },
};
</script>

<style scope>
</style>
