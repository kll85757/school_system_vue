/* eslint-disable */
<template>
  <div class="lessonDetail">
    <h3>无线网络技术</h3>
    <!-- <span>18章节 52课时</span> -->
    <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
      <el-tab-pane label="实验章节" name="first">
        <div>
          <ul>
            <li>
              <div class="listLess">
                <el-row :gutter="20">
                  <el-col :span="8">
                    <div class="grid-content bg-purple">索引</div>
                  </el-col>
                  <el-col :span="7">
                    <div class="grid-content bg-purple" />
                  </el-col>

                  <el-col :span="6">
                    <div class="grid-content bg-purple">实验报告：未提交</div>
                  </el-col>
                  <el-col :span="3">
                    <el-button
                      type="primary"
                      @click="toDoc"
                    >查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
            <li>
              <div class="listLess">
                <el-row :gutter="20">
                  <el-col :span="8">
                    <div class="grid-content bg-purple">
                      项目1无线网络应用概况的调研
                    </div>
                  </el-col>
                  <el-col :span="7">
                    <div class="grid-content bg-purple" />
                  </el-col>

                  <el-col :span="6">
                    <div class="grid-content bg-purple">实验报告：未提交</div>
                  </el-col>
                  <el-col :span="3">
                    <el-button
                      type="primary"
                      @click="toDoc"
                    >查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
            <li>
              <div class="listLess">
                <el-row :gutter="20">
                  <el-col :span="8">
                    <div class="grid-content bg-purple">
                      项目2AD-HOC无线对等网的构建
                    </div>
                  </el-col>
                  <el-col :span="7">
                    <div class="grid-content bg-purple" />
                  </el-col>

                  <el-col :span="6">
                    <div class="grid-content bg-purple">实验报告：未提交</div>
                  </el-col>
                  <el-col :span="3">
                    <el-button
                      type="primary"
                      @click="toDoc"
                    >查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
          </ul>
        </div>
      </el-tab-pane>
      <el-tab-pane label="授课计划" name="second">
        <div v-if="showPDF1">
          <pdf1 style="width: 100%; height: 100vh;" />
        </div>
      </el-tab-pane>
      <el-tab-pane label="课程标砖" name="third">
        <div v-if="showPDF2">
          <pdf1 style="width: 100%; height: 100vh;" />
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
// import pdf from 'vue-pdf'
// import PDFViewer from 'pdf-viewer-vue/dist/vue2-pdf-viewer'
// import VuePdfApp from 'vue-pdf-app'
// import this to use default icons for buttons
import pdf1 from './pdfs/pdf1.vue'
import 'vue-pdf-app/dist/icons/main.css'

export default {
  components: {
    pdf1
  },
  data() {
    return {
      showPDF1: false,
      showPDF2: false,
      activeName: 'first',
      // url: '@/assets/pdf.pdf',
      url: '../../assets/BlueTooth.pdf',
      url2: 'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf',
      url3: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf'
    }
  },
  mounted() {
    this.initPDFViewer()
  },
  methods: {
    initPDFViewer() {
      // 等待 Vue.js 渲染完成后再显示 PDFViewer
      this.$nextTick(() => {
        this.showPDF1 = true
        this.showPDF2 = true
        setTimeout(() => {
          window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
        }, 10)
      })
    },
    handleClick(tab, event) {
      this.showPDF1 = false
      this.showPDF2 = false
      console.log(tab, event)
      this.$nextTick(() => {
        this.showPDF1 = true
        this.showPDF2 = true
        setTimeout(() => {
          window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
        }, 10)
      })
    },
    toDoc(docName) {
      console.log(docName)
      this.$router.push('/lessondoc')
    },
    handleDownload() {
      console.log(11)
    }
  }
}
</script>
