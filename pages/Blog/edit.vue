<template>
  <div>
    <h2>{{ title }}</h2>
    <blog-create-edit/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Edit Blogs",
    };
  },
};
</script>

<style>
#species {
  width: 20%;
}
</style>
