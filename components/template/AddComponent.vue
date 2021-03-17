<template>
  <div>
    <h2>New Blogs</h2>
    <blog-create-edit />
  </div>
</template>
<script>
import axios from "axios";
import BlogCreateEdit from './BlogCreateEdit'
export default {
  components: {
    BlogCreateEdit
  }
};
</script>