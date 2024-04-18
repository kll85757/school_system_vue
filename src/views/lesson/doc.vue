/* eslint-disable */
<template>
  <div class="lessonDoc">
    <div class="docMenu">
      <el-row :gutter="20">
        <el-col :span="5">
          <el-button
            type="primary"
            icon="el-icon-arrow-left"
            @click="backTo"
          >返回</el-button>
        </el-col>
        <el-col :span="18">
          <div class="grid-content">项目1无线网络应用概况的调研</div>
        </el-col>
      </el-row>
    </div>
    <el-button style="margin-bottom: 10px;" icon="el-icon-menu" @click="toggleFormVisible" />

    <div v-show="formVisible" class="treeDoc">
      <h3>教学内容</h3>
      <el-tree
        :data="data"
        :props="defaultProps"
        @node-click="handleNodeClick"
      />
    </div>
    <div>
      <div v-if="show01">
        <pdf1 style="width: 100%; height: 100vh" />
      </div>
      <div v-if="show02">
        <pdf1 style="width: 100%; height: 100vh" />
      </div>
      <div v-if="show03">
        <pdf1 style="width: 100%; height: 100vh" />
      </div>
      <div v-if="video1">
        <video ref="videoPlayer" width="400" controls>
          <source
            src="https://www.bilibili.com/video/BV14h411Y7Qa?t=0.8"
            type="video/mp4"
          >
          浏览器版本过低
        </video>
      </div>
      <div v-if="video2">
        <video ref="videoPlayer" width="400" controls>
          <source
            src="https://www.bilibili.com/video/BV14h411Y7Qa?t=0.8"
            type="video/mp4"
          >
          浏览器版本过低
        </video>
      </div>
      <!-- <PDFViewer
        v-if="show01"
        source="/BlueTooth.pdf"
        style="height: 100vh; width: 80vw"
        @download="handleDownload"
      />
      <PDFViewer
        v-if="show02"
        source="/dummy.pdf"
        style="height: 100vh; width: 80vw"
        @download="handleDownload"
      />
      <PDFViewer
        v-if="show03"
        source="/BlueTooth.pdf"
        style="height: 100vh; width: 80vw"
        @download="handleDownload"
      /> -->
    </div>
  </div>
</template>
<script>
// import pdf from 'vue-pdf'
import pdf1 from './pdfs/pdf1.vue'

export default {
  components: {
    pdf1
  },
  data() {
    return {
      data: [
        {
          label: '课程文档'
        },
        {
          label: '教学ppt'
        },
        {
          label: '教学视频',
          children: [
            {
              label: '项目1'
            },
            {
              label: '项目2'
            }
          ]
        },
        {
          label: '实训题目'
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      },
      formVisible: false,
      show01: true,
      dayName: '',
      show02: false,
      show03: false,
      video1: false,
      video2: false,
      activeName: 'first',
      // url: '@/assets/pdf.pdf',
      url: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf',
      url2: 'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf',
      url3: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf'
    }
  },
  methods: {
    // 点击图标切换窗体可见性
    toggleFormVisible() {
      this.formVisible = !this.formVisible
    },
    // 关闭窗体
    closeFormDialog() {
      this.formVisible = false
    },
    handleClick(tab, event) {
      console.log(tab, event)
    },
    handleNodeClick(data) {
      console.log(data.label)
      switch (data.label) {
        case '课程文档':
          this.show01 = false
          this.show02 = false
          this.show03 = false
          this.$nextTick(() => {
            this.show01 = true
            this.show02 = false
            this.show03 = false
            setTimeout(() => {
              window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
            }, 1000)
          })

          break
        case '教学ppt':
          this.show01 = false
          this.show02 = false
          this.show03 = false
          this.$nextTick(() => {
            this.show01 = true
            this.show02 = false
            this.show03 = false
            setTimeout(() => {
              window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
            }, 1000)
          })
          break
        case '教学视频':
          this.dayName = '星期三'
          break
        case '项目1':
          this.show01 = false
          this.show02 = false
          this.show03 = false
          this.video1 = true
          this.video2 = false
          break
        case '项目2':
          this.show01 = false
          this.show02 = false
          this.show03 = false
          this.video1 = false
          this.video2 = true
          break
        case '实训题目':
          this.show01 = false
          this.show02 = false
          this.show03 = false
          this.$nextTick(() => {
            this.show01 = true
            this.show02 = false
            this.show03 = false
            setTimeout(() => {
              window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
            }, 100)
          })
          break
      }

      // this.$router.push("/lessondoc");
    },
    backTo() {
      this.$router.go(-1)
    },
    handleDownload() {
      console.log(11)
    }
  }
}
</script>
<style>
.lessonDoc {
  overflow: hidden;
}
</style>
