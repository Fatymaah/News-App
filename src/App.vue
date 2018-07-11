<template>
  <div class="container">
  

<div class="content" v-for = "article in news">

<img :src="article.urlToImage" alt="">

<h3>
  <strong>{{article.title}}</strong>
</h3>
<h4> Author | {{article.author}}</h4>

<p>{{article.description}}</p>

<a class="button" :href="article.url">Read More</a>



</div>


   
    

  </div>

</template>

<script>

const url ="https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=32af4be0ec3448f5b27b3ac282712df5";


import axios from 'axios'

const data = {
  news:[
  
  ]
  
}


export default {
  data: function() {
    return data
  },
  created(){
 this.loadNews();
  },
  methods:{
    loadNews() {
 axios.get(url).then(function(response) {
    console.log(response.data.articles)
    data.news = response.data.articles
  }).catch(function(error){
  consiole.log(error.message)
  })
  
  }
  
  }
}
</script>
