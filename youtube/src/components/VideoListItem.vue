<template>
  <li @click="selectedVideo" class="list">
      <img :src="video.snippet.thumbnails.high.url" :alt="video.snippet.title">
      <h3>{{ video.snippet.title }}</h3>
      <p>{{ video.snippet.description}}</p>
  </li>
</template>

<script>

export default {
    name: 'VideoListItem',
    props: {
        video: {
            type: Object,
            required: true
        }
    },
    methods: {
        selectedVideo() {
            // video-select-event $emit
            // 자식컴포넌트에서는 이벤트 발생(값 전달)
            this.$emit('video-select-event', this.video)
        }
    }
}

</script>
<style scoped>
img {
    width: 360px;
}
li {
    cursor: pointer;
}
li:hover {
    background-color: #fffff2;
}


</style>