<template>
  <div class="place">
    <img :src="img" width="235" height="300"/>
    <h1>{{ name }}</h1>
     <p>{{ desc }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: ['name', 'desc', 'img'],
};
</script>

<style scoped>
.place {
  display: flex;
  flex-direction: column;
  width: 280px;
  height: 320px;
  justify-content: center;
  background: white;
  border: 1px solid #ddd;
  padding: 20px 20px;
  margin: 10px;
}
</style>