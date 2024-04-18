<template>
  <div class="pdfView">
    <div>
      <PDFViewer
        :hide-thumbnails="thumbnailsHidden"
        :settings="{ defaultZoom: 200 }"
        source="/BlueTooth.pdf"
        style="height: calc(100vh - 100px); width: 100vw"
        @load="handleIframeLoad"
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
      thumbnailsHidden: false, // 控制预览区域的显示与隐藏
      url: '../../assets/BlueTooth.pdf',
      url2: 'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf',
      url3: 'http://storage.xuetangx.com/public_assets/xuetangx/PDF/PlayerAPI_v1.0.6.pdf'
    }
  },
  mounted() {
    this.initPDFViewer()
    this.$nextTick(() => {
      this.thumbnailsHidden = false // 在组件渲染完成后，隐藏预览区域
    })
  },
  created() {
    this.$nextTick(() => {
      this.hideCatalogScroller()
    })
  },
  methods: {
    hideCatalogScroller() {
      // 查找预览页（目录页）的容器元素并隐藏

      const scroller = document.querySelector('.scroller.catalog.visible')
      const iframe1 = document.getElementsByTagName('iframe')
      // 遍历所有的 iframe 元素
      for (let i = 0; i < iframe1.length; i++) {
        const iframe = iframe1[i]

        // 检查当前 iframe 是否加载完成（可以根据需要进一步判断）
        if (
          iframe.contentDocument &&
          iframe.contentDocument.readyState === 'complete'
        ) {
          // 在当前 iframe 中查找具有 .catalog 类的元素
          const catalogElement =
            iframe.contentDocument.querySelector('.catalog')

          // 如果找到了目标元素，则进行相应的操作
          if (catalogElement) {
            // 对目标元素进行操作，例如隐藏
            catalogElement.style.display = 'none'
          }
        }

        // if (
        //   iframe.contentDocument &&
        //   iframe.contentDocument.readyState === "complete"
        // ) {
        //   // 在当前 iframe 中查找符合特定选择器的元素，并设置样式
        //   const viewerItemDivs = iframe.contentDocument.querySelectorAll(
        //     ".viewer-container .scroller.viewer .viewer-content .viewer-item > div"
        //   );

        //   // 遍历所有符合条件的元素
        //   viewerItemDivs.forEach((div) => {
        //     // 设置元素的 margin 样式
        //     div.style.margin = "7px 10%";
        //   });
        // }
      }
      console.log(iframe1)
      console.log(iframe1)
      console.log(scroller)
      console.log(scroller)
      console.log(scroller)
      if (scroller) {
        scroller.style.display = 'none'
        console.log('预览页隐藏成功')
      }
    },
    handleIframeLoad() {
      const iframe = this.$refs.pdfIframe
      if (iframe && iframe.contentDocument) {
        const scroller = iframe.contentDocument.querySelector(
          '.scroller.catalog.visible'
        )
        if (scroller) {
          scroller.style.display = 'none'
        }
      }
    },
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
<style>
.pdfView {
  overflow: hidden;
}
</style>
