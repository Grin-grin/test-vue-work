<template>
  <FolderView name="$" :folders="folders" :files="files" image="img/folder.svg" :margin="0"/>
</template>

<script>
import FolderView from './components/FolderView.vue'
import data from './data/list';

export default {
  name: 'App',
  components: {
    FolderView
  },
  data: () => data
}
</script>

<style lang="scss">
#app {
  max-width: 1020px;
  margin-left: auto;
  margin-right: auto;
  background-color: #b9c9ec;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 25px;
}
</style>
