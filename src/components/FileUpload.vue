<template>
  <el-upload
      class="upload-demo"
      drag
      action="http://123.60.154.22:8080/image/upload"
      name="image"
      multiple
      :on-success="uploadSuccess"
  >
    <el-icon class="el-icon--upload"><upload-filled /></el-icon>
    <div class="el-upload__text">
      Drop file here or <em>click to upload</em>
    </div>
    <template #tip>
      <div class="el-upload__tip">
        jpg/png files with a size less than 500kb
      </div>
    </template>
  </el-upload>
  <div>
    <a :href="fileUrl" target="_blank">{{ fileUrl }}</a>
  </div>
</template>

<script setup>
import { UploadFilled } from '@element-plus/icons-vue'
</script>

<script>
export default {
  name: "FileUpload",
  data() {
    return {
      fileUrl: ""
    }
  },
  methods: {
    //上传文件成功
    uploadSuccess (response) {
      this.fileUrl = "http://123.60.154.22:8080/" + response.message
    }
  }
}
</script>

<style scoped>

</style>