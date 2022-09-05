<template>
  <div className="header">
    <h1>
      <span style="color: #41b883">Vue</span
      ><span style="color: #34495e">Tube</span>
    </h1>
    <h4>Search for videos from YouTube!</h4>
  </div>
</template>
<script>
export default {
  name: 'AppHeader',
};
</script>
<style scoped>
h1 {
  margin: 0;
  font-size: 4rem;
}
h4 {
  margin: 0;
}
.header {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-bottom: 50px;
}
</style>
