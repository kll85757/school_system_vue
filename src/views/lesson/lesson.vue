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
                    <el-button type="primary" @click="toDoc">查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
            <li>
              <div class="listLess">
                <el-row :gutter="20">
                  <el-col :span="8">
                    <div class="grid-content bg-purple">项目1无线网络应用概况的调研</div>
                  </el-col>
                  <el-col :span="7">
                    <div class="grid-content bg-purple" />
                  </el-col>

                  <el-col :span="6">
                    <div class="grid-content bg-purple">实验报告：未提交</div>
                  </el-col>
                  <el-col :span="3">
                    <el-button type="primary" @click="toDoc">查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
            <li>
              <div class="listLess">
                <el-row :gutter="20">
                  <el-col :span="8">
                    <div class="grid-content bg-purple">项目2AD-HOC无线对等网的构建</div>
                  </el-col>
                  <el-col :span="7">
                    <div class="grid-content bg-purple" />
                  </el-col>

                  <el-col :span="6">
                    <div class="grid-content bg-purple">实验报告：未提交</div>
                  </el-col>
                  <el-col :span="3">
                    <el-button type="primary" @click="toDoc">查看详情</el-button>
                  </el-col>
                </el-row>
              </div>
            </li>
          </ul>
        </div>
      </el-tab-pane>
      <el-tab-pane label="授课计划" name="second">
        <PDFViewer :source="url2" style="height: 100vh; width: 100vw" @download="handleDownload" />

      </el-tab-pane>
      <el-tab-pane label="课程标砖" name="third">
        <!-- <pdf ref="pdf" :src="url">
        </pdf> -->
        <PDFViewer :source="url" style="height: 100vh; width: 100vw" @download="handleDownload" />
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
// import pdf from 'vue-pdf'
import PDFViewer from 'pdf-viewer-vue/dist/vue2-pdf-viewer'

export default {
  components: {
    PDFViewer
  },
  data() {
    return {
      activeName: 'first',
      // url: '@/assets/pdf.pdf',
      url: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf',
      url2: 'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf',
      url3: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf'
    }
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event)
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
