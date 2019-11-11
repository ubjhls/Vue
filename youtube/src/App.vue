<template>
  <div id="app">
    <video-detail :video="selectVideo"></video-detail>
    <search-bar @input-change-event="onInputChange"></search-bar> <!-- 출력 -->
    <video-list @video-select-event="selectedVideo" :videos="videos"></video-list>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'  // 1-1. vue파일 불러오기
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = process.env.VUE_APP_API_KEY

export default {
  name: 'app',
  components: {
    VideoDetail,
    VideoList,
    SearchBar // component 등록
  },
  data() {
    return {
      videos: [],
      selectVideo: null
    } // SFC에서는 반드시 data는 함수로 작성하고, 오브젝트를 리턴하도록!
  },

  methods: {
    selectedVideo(video) {
      console.log('App도착')
      this.selectVideo = video
    },
    onInputChange(value) {
      console.log('==App==')
      console.log(value)
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          part: 'snippet',
          q: value
        }
      }).then(response => {
        console.log(response)
        // data의 videos에 저장
        this.videos = response.data.items
      })
      .catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
