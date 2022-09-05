<template>
  <div className="ui unstackable items">
    <VideoItem
      @select-video="$emit('select-video', video)"
      :video="video"
      :key="video.id"
      v-for="video in videos"
    />
  </div>
</template>

<script>
import VideoItem from './VideoItem.vue';

export default {
  name: 'VideoList',
  props: {
    videos: Array,
  },
  components: {
    VideoItem,
  },
  emits: ['select-video'],
};
</script>
