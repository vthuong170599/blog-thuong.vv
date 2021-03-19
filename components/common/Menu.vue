<template>
  <div>
    <ul class="list-group">
      <li class="list-group-item"><nuxt-link to="/Blog/list">Home</nuxt-link></li>
      <li class="list-group-item"><nuxt-link to="/Blog/search">Search</nuxt-link></li>
      <li class="list-group-item"><nuxt-link to="/Blog/add">New</nuxt-link></li>
      <li class="list-group-item"><nuxt-link :to="`/Blog/${1}`">Edit</nuxt-link></li>
    </ul>
  </div>
</template>
<style scoped>
    li{
        text-align: center;
    }
</style>