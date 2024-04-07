<template>
  <div class="dashboard-editor-container">
    <!-- <github-corner class="github-corner" /> -->

    <!-- <panel-group @handleSetLineChartData="handleSetLineChartData" /> -->

    <!-- <el-row style="background:#fff;padding:16px 16px 0;margin-bottom:32px;">
      <line-chart :chart-data="lineChartData" />
    </el-row> -->

    <div class="mainContent">
      <el-row :gutter="32">
        <el-col :xs="24" :sm="12" :lg="8">
          <div class="chartwrapper box1">
            <div>
              <h3>进入上次实验章节</h3>
              <br>
              <h3>项目5</h3>
              <p>无线网络技术</p>
            </div>
            <!-- <raddar-chart /> -->
          </div>
        </el-col>
        <el-col :xs="24" :sm="12" :lg="8">
          <div class="chartwrapper box2">
            <h3>我的成绩</h3>
            <br>
            <h3>成绩暂未公布</h3>
            <p><el-button round>查看成绩</el-button></p>
            <!-- <pie-chart /> -->
          </div>
        </el-col>
        <el-col :xs="24" :sm="12" :lg="8">
          <div class="chartwrapper box3">
            <h3>我的考试</h3>
            <br>
            <h3>暂无考试</h3>
            <!-- <p>无线网络技术</p> -->
            <!-- <bar-chart /> -->
          </div>
        </el-col>
      </el-row>
      <div class="lujin">
        <el-timeline>
          <el-timeline-item timestamp="学习路径" placement="top">
            <el-card>
              <h4>路由与交换 华三版</h4>
              <p>0%</p>
            </el-card>
          </el-timeline-item>
          <el-timeline-item timestamp="" placement="top">
            <el-card>
              <h4>路由与交换 华三版</h4>
              <p>0%</p>
            </el-card>
          </el-timeline-item>
          <el-timeline-item timestamp="" placement="top">
            <el-card>
              <h4>路由与交换 华三版</h4>
              <p>0%</p>
            </el-card>
          </el-timeline-item>
        </el-timeline>
      </div>

      <div class="tabBox">
        <el-tabs v-model="activeName" stretch="true" @tab-click="handleClick">
          <el-tab-pane label="基础课程" name="first">基础课程</el-tab-pane>
          <el-tab-pane label="核心课程" name="second">
            <el-card :body-style="{ padding: '0px', height: '300px' }">
              <img style="width: 100%;" src="@/assets/lesson1.png" class="image">
              <div style="padding: 14px">
                <span>无线网络技术</span>
                <br>
                <br>
                <div class="bottom clearfix">
                  <!-- <time class="time">{{ currentDate }}</time> -->
                  <el-button round class="button">18章节</el-button>
                  <el-button round type="primary" class="button">52课时</el-button>
                  <el-button round type="warning" class="button">老师</el-button>
                </div>
              </div>
            </el-card>
          </el-tab-pane>
          <el-tab-pane label="实训案例" name="third">实训案例</el-tab-pane>
        </el-tabs>
      </div>
    </div>

    <!-- <el-row :gutter="8">
      <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 12}" :xl="{span: 12}" style="padding-right:8px;margin-bottom:30px;">
        <transaction-table />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <todo-list />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <box-card />
      </el-col>
    </el-row> -->
  </div>
</template>

<script>
// import GithubCorner from '@/components/GithubCorner'
// import PanelGroup from './components/PanelGroup'
// import LineChart from './components/LineChart'
// import RaddarChart from './components/RaddarChart'
// import PieChart from './components/PieChart'
// import BarChart from './components/BarChart'
// import TransactionTable from './components/TransactionTable'
// import TodoList from './components/TodoList'
// import BoxCard from './components/BoxCard'

const lineChartData = {
  newVisitis: {
    expectedData: [100, 120, 161, 134, 105, 160, 165],
    actualData: [120, 82, 91, 154, 162, 140, 145]
  },
  messages: {
    expectedData: [200, 192, 120, 144, 160, 130, 140],
    actualData: [180, 160, 151, 106, 145, 150, 130]
  },
  purchases: {
    expectedData: [80, 100, 121, 104, 105, 90, 100],
    actualData: [120, 90, 100, 138, 142, 130, 130]
  },
  shoppings: {
    expectedData: [130, 140, 141, 142, 145, 150, 160],
    actualData: [120, 82, 91, 154, 162, 140, 130]
  }
}

export default {
  name: 'DashboardAdmin',
  components: {
    // GithubCorner,
    // PanelGroup,
    // LineChart,
    // RaddarChart,
    // PieChart,
    // BarChart
    // TransactionTable,
    // TodoList,
    // BoxCard
  },
  data() {
    return {
      lineChartData: lineChartData.newVisitis,
      activeName: 'second'
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.lineChartData = lineChartData[type]
    },
    handleClick(tab, event) {
      console.log(tab, event)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;
  min-height: 600px;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width: 1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
