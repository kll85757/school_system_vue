<template>
  <div class="">
    <div>
      <PDFViewer
        :settings="{ defaultZoom: 170 }"
        source="/BlueTooth.pdf"
        style="height: 100vh; width: 100vw"
        @download="handleDownload"
      />
    </div>
  </div>
</template>
<script>
// import pdf from 'vue-pdf'
import PDFViewer from 'pdf-viewer-vue/dist/vue2-pdf-viewer'
import 'vue-pdf-app/dist/icons/main.css'

export default {
  name: 'Pdf1',
  components: {
    PDFViewer
  },
  data() {
    return {
      showPDF: false,
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
        this.showPDF = true
        window.dispatchEvent(new Event('resize')) // 强制触发窗口大小改变事件
      })
    },
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
