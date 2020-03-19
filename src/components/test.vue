<template>
  <div class="hello">
      <input type="file" id="fileInput" />
      <el-button type="primary" @click="showFile">显示图片</el-button>
      <br/>
      <el-image :src="url"/>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      file:null,
      url:''
    }
  },
  methods: {
    showFile(){
      const f = document.getElementById("fileInput")
      console.log(f.files[0])
      const reader = new FileReader()
      reader.readAsDataURL(f.files[0])
      reader.onload = e => {
        console.log(e.target.result)
        this.url = e.target.result
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
