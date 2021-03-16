<template>
  <div>
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
        <tr v-for="blog in dataBlog" :key="blog.id">
          <td scope="row">{{ blog.id }}</td>
          <td>{{ blog.title }}</td>
          <td>{{ checkCate(blog.category)}}</td>
          <td>{{ blog.public }}</td>
          <td>{{ blog.position }}</td>
          <td>{{ blog.data_pubblic }}</td>
          <td><a class="btn btn-outline-success" @click="Edit()">Edit</a></td>
          <td><a class="btn btn-outline-danger">Delete</a></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
// import CATEGORY from '../constant/constant.js';
const CATEGORY = [
    {id:1,category:'thời sự'},
    {id:2,category:'thế giới'},
    {id:3,category:'kinh doanh'},
    {id:4,category:'giải trí'},
     {id:5,category:'thời sự'},
    {id:6,category:'thế giới'},
    {id:7,category:'kinh doanh'},
    {id:8,category:'giải trí'},
    {id:9,category:'thời sự'},
    {id:10,category:'thế giới'},
    {id:11,category:'kinh doanh'},
    {id:12,category:'giải trí'},
     {id:13,category:'thời sự'},
    {id:14,category:'thế giới'},
    {id:15,category:'kinh doanh'},
    {id:0,category:'giải trí'},
];
export default {
    mounted(){
        // console.log(CATEGORY);
        console.log(this.checkCate(1));
    },
    props: {
        dataBlog: {
            type: Array,
            default: ()=>[]
        }
    },
    data() {
        return {
            CATEGORY,
            cat: '',
        }
    },
    computed: {
        
    },
    methods: {
        checkCate(id){
            const lmao = this.CATEGORY.map(item => {
                if (item.id === id) {
                  return item.category
                }
                return ''
            })
            return lmao.join('')
            // const list = this.dataBlog.map(cate=>cate.category);
            // return list === CATEGORY.category
        }
        
    }
};
</script>