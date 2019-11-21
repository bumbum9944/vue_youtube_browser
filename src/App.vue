<template>
  <div class="container">
    youtube
    <!-- 3. 사용하기 -->
    <!-- <자식컴포넌트 @(v-on:)자식이 올려준 함수 = "부모가 사용할 함수"/> -->
    <!-- emit 올려주는 것 props는 내려주는 것 -->
    <SearchBar @inputChange="onInputChange"/>
    <VideoDetail :selectedVideo="selectedVideo"/>
    <!-- <자식컴포넌트 v-bind:자식한테 내려줄 이름="부모가가지고있는이름"/> -->
    <VideoList :videos="videos" @videoSelect="onVideoSelect"/>
  </div>
</template>

<script>
// 1. 가져오기
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'
import axios from 'axios'

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const API_URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  data: function(){
    return {
      videos: [],
      selectedVideo: null,
    }
  },
  name: 'App',
  // 2. 등록하기
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    onInputChange(inputValue){
      // console.log(inputValue)
      axios.get(API_URL, {
        params: {
          key: API_KEY,
          part: 'snippet',
          type: 'video',
          q: inputValue
        }
      })
      .then((response)=>{
        console.log(response)
        this.videos = response.data.items
      })
      .catch((error)=>{
        console.log(error)
      })
    },
    onVideoSelect(video){
      console.log(video)
      this.selectedVideo = video
    }
  }
}
</script>

<style>

</style>