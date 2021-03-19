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
    <button class="btn btn-success mb4" @click="SendKeyWord()">Search</button>
  </div>
</template>
<script>
// import axios from "axios";
export default {
  data() {
    return {
      Search: '',
    };
  },
  methods: {
    /** send data of blog to the search page
     * @since 19-3-2021
     */
    SendKeyWord() {
      this.$emit('sendKeyWord', this.Search);
    },
  },
};
</script>