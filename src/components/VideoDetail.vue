<template>
  <div>
    <div className="ui embed">
      <iframe
        title="video-player"
        :src="`https://www.youtube.com/embed/${video.id.videoId}`"
      />
    </div>
    <div className="ui segment">
      <h4 className="ui header">{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>
Z

<script>
export default {
  name: 'VideoDetail',
  props: {
    video: Object,
  },
};
</script>
