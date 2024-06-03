<template>
  <div id="app">
    <h1>Cluster List</h1>
    <ul>
      <li v-for="cluster in clusters" :key="cluster.id">{{ cluster.name }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      clusters: []
    };
  },
  created() {
    axios.get('/v3/clusters').then(response => {
      this.clusters = response.data.data;
    });
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>