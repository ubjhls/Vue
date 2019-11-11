<template>
  <div>
      <h2>영상 목록</h2>
      <video-list-item v-for="video in videos" 
      :key="video.id.videoId" 
      :video="video" 
      @video-select-event="selectedVideo">
      </video-list-item>
      <!-- 부모컴포넌트에서는 이벤트 listen(v-on)
            원하는 메소드 실행 -->
  </div>
</template>

<script>
import VideoListItem from './VideoListItem.vue'
export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: {
            type: Array,
            required: true
        }
    },
    methods: {
        selectedVideo(video) {
            console.log('리스트로 왔당')
            this.$emit('video-select-event', video)
        }
    },
}
</script>

<style>

</style>