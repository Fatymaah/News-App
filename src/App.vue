<template>
  <div class="container">
  <div class="search">
  
    <input type="search" placeholder="Search" id="nameField" v-model="search">
  
    
    <button class="button" href="#" v-on:click="loadNews" type="button">Search</button>
    <p v-if="loading">Loading ...</p>
    <div class="lds-spinner" v-if="loading"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
</div>

<div class="content" v-for = "article in news">

<img v-if="article.urlToImage" :src="article.urlToImage" alt="">

<h3>
  <strong>{{article.title}}</strong>
</h3>
<h4> Author | {{article.author}}</h4>

<p>{{article.description}}</p>

<a class="button" :href="article.url" target="_blank">Read More</a>



</div>






   
    

  </div>

</template>

<script>
const baseurl = "https://newsapi.org/v2";
const apiKey = "32af4be0ec3448f5b27b3ac282712df5";
const endpoint ="/everything";


import axios from 'axios'

const data = {
  news:[
  
  ],
  search:"",
  loading:false
  
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
      if(this.search.length < 1){
        return;
      }
      this.loading = true;
      this.news = [];
      let url = baseurl + endpoint + "?q=" + this.search + '&apiKey=' + apiKey;
 axios.get(url).then(function(response) {
    console.log(response.data.articles)
    data.loading=false;
    data.news = response.data.articles
  }).catch(function(error){
  console.log(error.message)
  })
  
  }
  
  }
}
</script>
