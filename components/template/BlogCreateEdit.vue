<template>
  <div>
    <p v-if="err.length > 0">{{ err }}</p>
    <div class="col-md-8">
      <div>
        <div class="form-group">
          <label for="title">Tiêu đề</label>
          <input
            type="text"
            class="form-control"
            name=""
            id="title"
            aria-describedby="helpId"
            placeholder="Tiêu đề"
            v-model="blogs.title"
          />
        </div>
        <div class="form-group">
          <label for="desc">Mô tả ngắn</label>
          <input
            type="text"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
            v-model="blogs.des"
          />
        </div>
        <div class="form-group">
          <label for="detail">chi tiết</label>
          <textarea
            class="form-control"
            name=""
            id="detail"
            rows="6"
            placeholder="chi tiết"
            v-model="blogs.detail"
          ></textarea>
        </div>
        <div class="form-group">
          <label for="desc">Hình ảnh</label>
          <input
            type="file"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
          />
        </div>
        <div class="form-group">
          <label for="species">loại</label>
          <select
            class="form-control"
            name=""
            id="species"
            v-model="blogs.category"
          >
            <option
              v-for="(cate, index) in CATEGORY"
              :key="index"
              :value="cate.id"
            >
              {{ cate.category }}
            </option>
          </select>
        </div>
        <div class="form-group">
          <p>Vị trí</p>
          <ul class="list-group list-group-flush">
            <li
              v-for="(post, key) in POSITION"
              v-bind:key="post"
              class="list-group-control"
            >
              <div class="custom-control custom-checkbox">
                <input
                  type="checkbox"
                  :value="key"
                  class="custom-control-input"
                  :id="'check' + key"
                  v-model="blogs.position"
                />
                <label class="custom-control-label" :for="'check' + key">{{
                  post
                }}</label>
              </div>
            </li>
          </ul>
        </div>
        <div class="form-group">
          <label class="bold">Public</label><br />
          <input
            type="radio"
            id="checkbox1"
            :value="yes"
            v-model="blogs.public"
          />
          <label for="checkbox1">Yes</label><br />
          <input
            type="radio"
            id="checkbox2"
          :value="no"
            v-model="blogs.public"
          />
          <label for="checkbox2">No</label><br />
        </div>
        <div class="form-group mt-3">
          <label for="desc">Date public</label>
          <input
            style="width: 30%"
            type="date"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
            v-model="blogs.data_pubblic"
          />
        </div>
        <div style="margin-left: 45%; margin-bottom: 10%">
          <button
            type="submit"
            v-show="ShowAdd"
            class="btn btn-success"
            @click="addBog()"
          >
            Add
          </button>
          <button
            type="submit"
            v-show="showEdit"
            class="btn btn-success"
            @click="updateBlog(blogs.id)"
          >
            Edit
          </button>
          <button type="button" class="btn btn-primary">Clear</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
const CATEGORY = [
  { id: 0, category: "cat1" },
  { id: 1, category: "thời sự" },
  { id: 2, category: "thế giới" },
  { id: 3, category: "kinh doanh" },
  { id: 4, category: "giải trí" },
  { id: 5, category: "thời sự" },
  { id: 6, category: "thế giới" },
  { id: 7, category: "kinh doanh" },
  { id: 8, category: "giải trí" },
  { id: 9, category: "thời sự" },
  { id: 10, category: "thế giới" },
  { id: 11, category: "kinh doanh" },
  { id: 12, category: "giải trí" },
  { id: 13, category: "thời sự" },
  { id: 14, category: "thế giới" },
  { id: 15, category: "kinh doanh" },
];
const POSITION = ["Việt Nam", "Châu Á", "Châu Âu", "Châu Mỹ"];
export default {
  name: "blog-create-edit",
  data() {
    return {
      yes: true,
      no: false,
      ShowAdd: true,
      showEdit: false,
      CATEGORY,
      POSITION,
      blogs: {
        id: "",
        title: "",
        des: "",
        detail: "",
        category: "",
        public: true,
        data_pubblic: "",
        position: [],
        thumbs: "",
      },
      err: [],
    };
  },
  methods: {
    // function add blog
    addBog() {
      this.err = [];
      // validate
      if (this.blogs.title == "") {
        this.err.push("title không được để trống");
      }
      if (this.blogs.des == "") {
        this.err.push("Mô tả không được để trống");
      }
      if (this.blogs.detail == "") {
        this.err.push("Chi tiết không được để trống");
      }
      if (this.blogs.data_pubblic == "") {
        this.err.push("data_pubblic không được để trống");
      }
      if (this.blogs.position == "") {
        this.err.push("position không được để trống");
      }
      console.log(this.err.length);
      if (this.err.length > 0) {
        return false;
      } else {
        axios.post("http://localhost:3001/blogs", this.blogs).then((res) => {
          console.log("them thanh cong");
        });
        this.$router.push("/Blog/list");
      }
    },

    // get data by id
    getBlogByID(id) {
      axios
        .get("http://localhost:3001/blogs/" + id)
        .then((res) => (this.blogs = res.data));
    },

    // function update blog
    updateBlog(id) {
      this.err = [];
      // validate
      if (this.blogs.title == "") {
        this.err.push("title không được để trống");
      }
      if (this.blogs.des == "") {
        this.err.push("Mô tả không được để trống");
      }
      if (this.blogs.detail == "") {
        this.err.push("Chi tiết không được để trống");
      }
      if (this.blogs.data_pubblic == "") {
        this.err.push("data_pubblic không được để trống");
      }
      if (this.blogs.position == "") {
        this.err.push("position không được để trống");
      }
      if (this.err.length > 0) {
        return false;
      } 
      else {
        axios
          .put("http://localhost:3001/blogs/" + id, this.blogs)
          .then((res) => {
            console.log("sua thanh cong " + id);
          });
        axios.get("http://localhost:3001/blogs").then((res) => {
          this.dataBlog = res.data;
        });
        this.$router.push("/Blog/list");
      }
    },
  },
  mounted() {
    if (this.$route.params.id != null) {
      this.getBlogByID(this.$route.params.id);
      this.showEdit = !this.showEdit;
      this.ShowAdd = !this.ShowAdd;
    }
  },
};
</script>
<style scoped>
.list-group {
  list-style: none;
}
</style>