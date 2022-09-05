<template>
  <div className="ui container mt-1">
    <AppHeader />
    <SearchBar @on-search="onSearch" />
    <div v-if="videos.length" className="ui segment">
      <div className="ui padded grid">
        <div className="ui row">
          <div className="sixteen wide tablet ten wide computer column">
            <VideoDetail :video="selectedVideo" />
          </div>
          <div className="sixteen wide tablet six wide computer column">
            <VideoList @select-video="selectVideo" :videos="videos" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VideoDetail from './components/VideoDetail.vue';
import VideoList from './components/VideoList.vue';
import SearchBar from './components/SearchBar.vue';
import AppHeader from './components/AppHeader.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    VideoDetail,
    VideoList,
    SearchBar,
    AppHeader,
  },

  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    async fetchData(term) {
      const res = await axios.get(
        'https://www.googleapis.com/youtube/v3/search',
        {
          params: {
            q: term,
            part: 'snippet',
            type: 'video',
            maxResults: 5,
            key: process.env.VUE_APP_YOUTUBE_API_KEY,
          },
        }
      );
      return res.data.items;
    },
    async onSearch(e, text) {
      e.preventDefault();
      const data = await this.fetchData(text);
      this.videos = data;
      this.selectedVideo = data[0];
    },
    selectVideo(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
<style scoped>
.container {
  margin-top: 20px;
}
.column {
  padding-top: 1rem;
  padding-bottom: 1rem;
}
</style>
