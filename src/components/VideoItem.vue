<template>
  <div className="item item-container" @click="$emit('select-video', video)">
    <div className="image">
      <img alt="" :src="video.snippet.thumbnails.medium.url" />
    </div>
    <div className="content">
      <div className="header">{{ video.snippet.title }}</div>

      <div className="description">
        <p></p>
      </div>
      <div className="extra">Channel : {{ video.snippet.channelTitle }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoItem',
  props: {
    video: Object,
  },
};
</script>

<style scoped>
.item-container :hover {
  cursor: pointer;
}
.item {
  word-break: break-word;
}
</style>
