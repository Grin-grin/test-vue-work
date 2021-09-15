<template>
  <p class="folder"
    :style="[{backgroundImage: 'url(' + image  + ')'}, folderTransform]"
    @click="toggleChildren"
    :class="childrenClasses"
    
  >
    {{name}}
  </p>
  <template v-for="folder in folders" :key="folder">
    <FolderView
      v-if="showchildren"
      :name="folder.name"
      :folders="folder.folders"
      :files="folder.files"
      :image="folder.image"
      :margin="margin + 1"
    />
  </template>
  <div :style="[
    {display: 'flex'},
    {flexWrap: 'wrap'},
    {width: '800px'},
    {justifyContent: 'space-between'},
    fileTransform
  ]">
    <template v-for="file in files" :key="file">
      <FileView
        v-if="showchildren"
        :name="file.name"
        :image="file.image"
      />
    </template>
  </div>
</template>

<script>
import FileView from "./FileView";
export default {
  name: 'FolderView',
  components: {FileView},
  props: [
    'name',
    'folders',
    'files',
    'image',
    'margin',
  ],
  data() {
    return {
      showchildren: false
    };
  },
  computed: {
    childrenClasses() {
      return {'children': this.folders || this.files }
    },
    folderTransform() {
      return {transform: `translate(${this.margin * 50}px)`}
    },
    fileTransform() {
      return {transform: `translate(${(this.margin + 1) * 50}px)`}
    }
  },
  methods: {
    toggleChildren() {
      this.showchildren = !this.showchildren;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.folder{
  margin: 0 0 20px 50px;
  padding-top: 20px;
  display: flex;
  width: 200px;
  height: 220px;
  align-items: flex-end;
  justify-content: center;
  color: orangered;
  background-position: 0 20px;
  background-repeat: no-repeat;
  background-size: contain;
  border-bottom: 1px solid #000;
}
.children {
  cursor: pointer;
}
</style>
