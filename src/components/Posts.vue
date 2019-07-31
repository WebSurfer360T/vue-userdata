<template>
  <div class="">
    <table class="table table-striped mt-4">
      <thead>
      <tr>
        <th scope="col">User Id</th>
        <th scope="col">Title</th>
        <th scope="col">Body</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="post in posts" :key="post.id">
        <td >{{post.id}}</td>
        <td >{{post.title}}</td>
        <td>{{post.body}}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
    table {
  border: 1px solid #ccc;
  border-collapse: collapse;
  table-layout: fixed;
  width: 80%;
  margin: 0 auto;
}
table tr {
  border: 1px solid #ddd;
  padding: .35em;
  text-align: center;
}
table tr:nth-child(even) {
  background: #f8f8f8;  
}
table th,
table td {
  padding: 10px;
  text-align: center;
}
table th {
  background: #00007f;
  color: #fff;
  font-size: .85em;
  letter-spacing: .1em;
  text-transform: uppercase;
}
table td {
  white-space:normal;
  overflow: hidden;
  text-overflow:ellipsis;
  text-align: center;
}
</style>

<script>
  import axios from 'axios'

  export default{
      name: 'PostsExample',
      data(){

          return {

            posts: []

          }
      },

    created(){
        axios.get('https://jsonplaceholder.typicode.com/posts').then(posts=>{
            this.posts = posts.data
        });
    }
  }
</script>

