<template>
  <el-row>
    <el-col :span="8"></el-col>
    <el-col :span="8">
      <div>
        <h1>Image Upload</h1>
      </div>
    </el-col>
    <el-col :span="8"></el-col>
  </el-row>

  <el-row>
    <el-col :span="8"></el-col>
    <el-col :span="8">
      <el-upload class="upload-demo" drag action="http://121.36.241.84:80/images-land/image/upload" name="image" :limit="1"
      :show-file-list="false"
        :multiple="false" :before-upload="beforeAvatarUpload" :on-success="uploadSuccess">
        <el-icon class="el-icon--upload"><upload-filled /></el-icon>
        <div class="el-upload__text">
          拖拽到此 或者 <em>点击上传</em>
        </div>
        <template #tip>
          <div class="el-upload__tip">
            jpg/png图片, 小于5MB
          </div>
        </template>
      </el-upload>
    </el-col>
    <el-col :span="8"> </el-col>
  </el-row>
  <br>
  <el-row>
    <el-col :span="8"></el-col>
    <el-col :span="8">
      <div>
        <p>图片链接: <el-link :href="fileUrl" type="primary" target="_blank">{{ fileUrl }}</el-link></p>
      </div>
      <div>
        <p>Markdown语法: </p>
        <el-input
          v-model="markDown"
          :rows="2"
          type="textarea"
          placeholder=""
        />
      </div>
      <div>
        <p>HTML语法: </p>
        <el-input
          v-model="html"
          :rows="2"
          type="textarea"
          placeholder=""
        />
      </div>
    </el-col>
    <el-col :span="8"></el-col>
  </el-row>

</template>

<script setup>
import { UploadFilled } from '@element-plus/icons-vue'
import { ElMessage } from 'element-plus'
</script>

<script>
export default {
  name: "FileUpload",
  data() {
    return {
      fileUrl: "",
      markDown: "",
      html: "",
    }
  },
  methods: {
    beforeAvatarUpload(rawFile) {
      console.log(rawFile.type)
      if (rawFile.type !== 'image/jpeg' && rawFile.type !== 'image/png') {
        ElMessage.error('图片格式错误!')
        return false
      }
      if (rawFile.size / 1024 / 1024 > 5) {
        ElMessage.error('图片大小超过 5MB!')
        return false
      }
      return true
    },
    //上传文件成功
    uploadSuccess(response) {
      ElMessage.success('上传成功！')
      this.fileUrl = "http://123.60.154.22:8080/" + response.message
      this.markDown = "![图片alt](" + this.fileUrl + "  \"图片title\")"
      this.html = "<img src=\"" + this.fileUrl + "\" alt=\"图片alt\" title=\"图片title\">"
    }
  }
}
</script>

<style scoped></style>