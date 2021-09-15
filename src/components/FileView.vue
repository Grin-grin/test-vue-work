<template>
  <p class="file" :style="{backgroundImage: 'url(' + image  + ')'}">{{name}}</p>
</template>

<script>
export default {
  name: 'FileView',
  props: {
    name: String,
    image: String,
  }
}
</script>

<style scoped lang="scss">
.file{
  margin: 50px 0 20px 50px;
  display: flex;
  width: 210px;
  height: 240px;
  align-items: flex-end;
  justify-content: center;
  color: green;
  background-repeat: no-repeat;
  background-size: contain;
}
</style>
