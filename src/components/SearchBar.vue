<template>
  <div className="search-bar ui segment">
    <form className="ui form" @submit="$emit('on-search', $event, text)">
      <div className=" field">
        <div class="ui icon input">
          <input
            placeholder="Search videos..."
            type="text"
            v-model="text"
            class="prompt"
          />
          <i
            class="inverted circular search link icon"
            @click="$emit('on-search', $event, text)"
          ></i>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      text: '',
    };
  },
};
</script>
