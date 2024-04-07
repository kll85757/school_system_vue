<template>
  <div class="app-container documentation-container">
    <div style="width: 100%">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="">
          <el-select v-model="formInline.region" placeholder="选择学期">
            <el-option label="学期1" value="shanghai" />
            <el-option label="学期2" value="beijing" />
          </el-select>
        </el-form-item>
        <el-form-item label="">
          <el-input v-model="formInline.user" placeholder="课程名称" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">搜索</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div>
      <el-row>
        <el-col v-for="(o, index) in 3" :key="o" :span="7" :offset="index > 0 ? 1 : 0">
          <a @click="toDetail">
            <el-card class="cardLess" :body-style="{ padding: '0px' }">
              <img style="width: 100%;" src="@/assets/lesson1.png" class="image">
              <div style="padding: 14px;">
                <h3>第二学期</h3>
                <span>无线网络技术</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button">授课 ： 张老师</el-button>
                </div>
              </div>
            </el-card>
          </a>
        </el-col>
      </el-row>
    </div>

  </div>
</template>

<script>
// import DropdownMenu from '@/components/Share/DropdownMenu'

export default {
  name: 'Guide',
  // components: { DropdownMenu },
  data() {
    return {
      formInline: {
        user: '',
        region: ''
      },
      activeName: 'first',
      reverse: false,
      tableData: [{
        pf: '2024-05-02',
        cj: '85',
        time: '2024-05-01',
        name: '单元测试01',
        tiku: '计算机网络2021题库'
      }, {
        pf: '2024-05-02',
        cj: '85',
        time: '2024-05-01',
        name: '单元测试02',
        tiku: '计算机网络2021题库'
      }, {
        pf: '2024-05-02',
        cj: '88',
        time: '2024-05-01',
        name: '单元测试03',
        tiku: '计算机网络2021题库'
      }, {
        pf: '2024-05-02',
        cj: '75',
        time: '2024-05-01',
        name: '单元测试04',
        tiku: '计算机网络2021题库'
      }],
      activities: [
        {
          content: '',
          timestamp: '2018-04-15'
        },
        {
          content: '',
          timestamp: '2018-04-16'
        }
      ]
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    },
    toDetail() {
      this.$router.push({ path: '/lessonDetail' })
    }
  }
}
</script>

<style lang="scss" scoped>
.documentation-container {
  // margin: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;

  .document-btn {
    flex-shrink: 0;
    display: block;
    cursor: pointer;
    background: black;
    color: white;
    height: 60px;
    padding: 0 16px;
    margin: 16px;
    line-height: 60px;
    font-size: 20px;
    text-align: center;
  }
}
</style>
