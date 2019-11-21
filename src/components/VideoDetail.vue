<template>
<!-- show로하면 디스플레이 옵션에서 안보이고 if는 랜더링 조차 안됨 -->
  <div v-if="selectedVideo">
    <div>
      <iframe :src="videoURL" frameborder="0"></iframe>
      <h4>{{selectedVideo.snippet.title}}</h4>
      <p>{{selectedVideo.snippet.description}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: {
    selectedVideo: Object
  },
  computed: {
    videoURL (){
      const videoID = this.selectedVideo.id.videoId
      return `https://www.youtube.com/embed/${videoID}`
    }
  }
}
</script>

<style>

</style>