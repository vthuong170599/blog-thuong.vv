<template>
  <div class="container">
    <div class="header">
      <Header></Header>
    </div>
    <div class="row">
      <div class="col-md-3">
        <Menu />
      </div>
      <div class="col-md-9">
        <Nuxt />
      </div>
    </div>
  </div>
</template>
<script>
import Header from "../components/common/Header";
import Menu from "../components/common/Menu";
export default {
  components: {
    Header,
    Menu
  }
};
</script>
<style>
.content {
  width: 100%;
  height: auto;
  margin-top: 100px;
}
.header {
  display: flex;
  width: 100%;
  height: 100px;
  margin: 20px 0;
}
.menua {
  width: 30%;
  margin-top: 20px;
  margin-left: -10px;
  height: 100px;
}
.content1 {
  width: 100%;
  height: auto;
}
.table tr th,
.table tr,
td {
  text-align: center;
  border: 1px solid black;
}
</style>
