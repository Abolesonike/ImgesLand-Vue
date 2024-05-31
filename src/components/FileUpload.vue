<template>
  <el-upload
      class="upload-demo"
      drag
      action="http://127.0.0.1:8080/image/upload"
      name="image"
      multiple
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
</template>

<script setup>
import { UploadFilled } from '@element-plus/icons-vue'
</script>

<script>
export default {
  name: "FileUpload",
  methods: {
  }
}
</script>

<style scoped>

</style>