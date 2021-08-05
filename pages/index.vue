<template>
  <div class="container">
      <h1>Holis soy la pagina index , aca va lo que trae la api:</h1>

       <ul>
         <li v-for="post of posts">
          <div class="post">
             <h3>{{ post.title }}</h3>
             <body>{{ post.body }}</body>
          </div>
         </li>
       </ul>
       
  </div>
</template>

<script>


import axios from 'axios'

export default {

  data(){
    return{
      posts: []
    }
  },

  async created(){
    try{
     const res = await axios.get('https://jsonplaceholder.typicode.com/posts')
     console.log(res);
     this.posts = res.data;

    }catch(error){
      console.log(error)
    }

  }

}
</script>

<style>
  body{
    background-color: #2d3436;
    color: whitesmoke;
  }

  .post{
    padding:  1rem;
    border: 5px;
    margin: 1rem;
  }
</style>
