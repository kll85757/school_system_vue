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
    <div class="treeDoc">
      <h3>教学内容</h3>
      <el-tree
        :data="data"
        :props="defaultProps"
        @node-click="handleNodeClick"
      />
    </div>
    <div style="width: 80%">
      <PDFViewer
        source="/BlueTooth.pdf"
        style="height: 100vh; width: 80vw"
        @download="handleDownload"
      />
    </div>
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
      data: [
        {
          label: '课程文档',
          children: [
            {
              label: '二级 1-1',
              children: [
                {
                  label: '三级 1-1-1'
                }
              ]
            }
          ]
        },
        {
          label: '教学PPT',
          children: [
            {
              label: '二级 2-1',
              children: [
                {
                  label: '三级 2-1-1'
                }
              ]
            },
            {
              label: '二级 2-2',
              children: [
                {
                  label: '三级 2-2-1'
                }
              ]
            }
          ]
        },
        {
          label: '课时',
          children: [
            {
              label: '二级 3-1',
              children: [
                {
                  label: '三级 3-1-1'
                }
              ]
            },
            {
              label: '二级 3-2',
              children: [
                {
                  label: '三级 3-2-1'
                }
              ]
            }
          ]
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      },
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
    handleNodeClick(data) {
      console.log(data)
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
