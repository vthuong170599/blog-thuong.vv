<template>
  <div>
    <div class="col-md-8">
      <div>
        <div class="form-group">
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.title }}
          </p>
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
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.des }}
          </p>
          <label for="desc">Mô tả ngắn</label>
          <textarea
            class="form-control"
            name=""
            id="desc"
            rows="6"
            placeholder="mô tả ngắn"
            v-model="blogs.des"
          ></textarea>
        </div>
        <div class="form-group">
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.detail }}
          </p>
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
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.category }}
          </p>
          <label for="species">loại</label>
          <select
            class="form-control"
            name=""
            id="species"
            v-model="blogs.category"
          >
            <option
              v-for="(cate, index) in getCate()"
              :key="index"
              :value="index"
            >
              {{ cate }}
            </option>
          </select>
        </div>
        <div class="form-group">
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.position }}
          </p>
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
            :value="1"
            v-model="blogs.public"
          />
          <label for="checkbox1">Yes</label><br />
          <input
            type="radio"
            id="checkbox2"
            :value="0"
            v-model="blogs.public"
          />
          <label for="checkbox2">No</label><br />
        </div>
        <div class="form-group mt-3">
          <p v-if="Object.keys(err).length > 0" class="text text-danger">
            {{ err.data_pubblic }}
          </p>
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
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import { CATEGORY } from "../../constant/constant";
import { POSITION } from "../../constant/constant";
import swal from "sweetalert2";
export default {
  name: "blog-create-edit",
  data() {
    return {
      yes: true,
      no: false,
      ShowAdd: true,
      showEdit: false,
      CATEGORY: CATEGORY,
      POSITION: POSITION,
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
      err: {},
    };
  },
  methods: {
    /** delete Blog by id
     * @return array CATEGORY
     *
     * @since 18-3-2021
     */
    getCate() {
      return this.CATEGORY;
    },

    /** delete Blog by id
     * @return array POSITION
     *
     * @since 18-3-2021
     */
    getPosition() {
      return this.POSITION;
    },

    /** validatation update and create
     *
     * @since 18-3-2021
     */
    validateBlog() {
      this.err = {};
      if (this.blogs.title == "") {
        this.err.title = "title không được để trống";
      }
      if (this.blogs.des == "") {
        this.err.des = "Mô tả không được để trống";
      }
      if (this.blogs.detail == "") {
        this.err.detail = "Chi tiết không được để trống";
      }
      if (this.blogs.data_pubblic == "") {
        this.err.data_pubblic = "data_pubblic không được để trống";
      }
      if (this.blogs.position == "") {
        this.err.position = "position không được để trống";
      }
    },

    /** create data in blog
     *
     * @since 18-3-2021
     */
    addBog() {
      this.validateBlog();
      if (Object.keys(this.err).length > 0) {
        return this.err;
      } else {
        axios.post("http://localhost:8000/api/blog", this.blogs).then((res) => {
          swal.fire({
            position: "center",
            icon: "success",
            title: "insert successfully",
            showConfirmButton: false,
            timer: 1500,
          });
          this.$router.push("/Blog/list");
        });
      }
    },

    /** get data of blog by id
     * @param  id id for element Blog
     *
     * @since 18-3-2021
     */
    getBlogByID(id) {
      axios
        .get("http://localhost:8000/api/blog/" + id)
        .then((res) => (this.blogs = res.data));
    },

    /** update data of blog by id
     * @param  id id for element Blog
     *
     * @since 18-3-2021
     */
    updateBlog(id) {
      this.validateBlog();
      if (Object.keys(this.err).length > 0) {
        return this.err;
      } else {
        axios
          .put("http://localhost:8000/api/blog/" + id, this.blogs)
          .then((res) => {
            console.log("sua thanh cong " + id);
            this.$router.push("/Blog/list");
            swal.fire({
              position: "center",
              icon: "success",
              title: "update successfully",
              showConfirmButton: false,
              timer: 1500,
            });
          });
      }
    },
  },
  mounted() {
    /** check param id of router
     * @param  id id for element Blog
     *
     * @since 18-3-2021
     */
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