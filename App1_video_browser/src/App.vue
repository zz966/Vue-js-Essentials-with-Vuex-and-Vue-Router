<template>
  <div class="container">
   <SearchBar  @termChange="onTermChange"/>
   <div class="row">
     <p id="errorMessage"></p>
     <VideoDetail :video="selectedVideo"></VideoDetail>
     <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList> 
   </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'

const API_KEY ="{replace with your YouTube API_KEY}";


export default {
  name: 'App',
  components:{
    SearchBar,
    VideoList,
    VideoDetail
  },
  data(){
    return {
      videos:[],
      selectedVideo:null,
     
    };
  },
  methods:{
    onVideoSelect(video){
      this.selectedVideo = video;
    },

    onTermChange(searchTerm){
        axios.get('https://www.googleapis.com/youtube/v3/search',{
          params:{
            key:API_KEY,
            type:'video',
            part:'snippet',
            q:searchTerm
          }
        }).then(Response=>{
          this.videos = Response.data.items  //response.data.items is the data from the request of API.
        }).catch(function(error){
            if (error.response) {
            
                console.log(error.response.data);
                document.getElementById("errorMessage").innerHTML=
                 " Error message: " +error.response.data.error.message +"   error code: " +error.response.data.error.code;
                
            }
        });
    }

  }
}


</script>

<style scoped>

    #errorMessage{
        text-align: center;
        margin:20px;
    }

    .row{
      flex-wrap: nowrap;
    }

</style>
