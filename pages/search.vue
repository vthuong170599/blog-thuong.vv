<template>
  <div>
    <h2>{{ titlePage }}</h2>
    <form>
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
            />
          </div>
        </div>
      </div>
      <button type="submit" class="btn btn-success">Search</button>
    </form>
    <h2 class="mt-5">{{titleTable}}</h2>
   <List-blog/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titlePage: "Search Blogs",
      titleTable: "List Blogs",
    };
  },
};
</script>

<style scope>
form {
    margin-top: 3%;
}
</style>
