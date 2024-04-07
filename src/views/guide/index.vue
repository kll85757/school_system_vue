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
          <el-input v-model="formInline.user" placeholder="试卷名称" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">搜索</el-button>
        </el-form-item>
      </el-form>
    </div>
    <el-tabs v-model="activeName" style="width: 100%" @tab-click="handleClick">
      <el-tab-pane label="实验报告" name="first">
        <div style="width: 100%">
          <el-table :data="tableData" stripe style="width: 100%">
            <el-table-column prop="tiku" label="报告名称" width="180" />
            <!-- <el-table-column prop="name" label="试卷名称" width="180">
            </el-table-column>
            <el-table-column prop="time" label="考试时间"> </el-table-column>
            <el-table-column prop="pf" label="评分时间"> </el-table-column>
            <el-table-column prop="cj" label="成绩"> </el-table-column> -->
            <el-table-column prop="" label="操作" />
          </el-table>
        </div>
      </el-tab-pane>
      <el-tab-pane label="实验测评" name="second">
        <div style="width: 100%">
          <el-table :data="tableData" stripe style="width: 100%">
            <!-- <el-table-column prop="tiku" label="关联题库" width="180">
            </el-table-column> -->
            <el-table-column prop="name" label="实验名称" width="180" />
            <!-- <el-table-column prop="time" label="考试时间"> </el-table-column>
            <el-table-column prop="pf" label="评分时间"> </el-table-column>
            <el-table-column prop="cj" label="成绩"> </el-table-column> -->
            <el-table-column prop="" label="操作" />
          </el-table>
        </div>
      </el-tab-pane>
      <el-tab-pane label="考试成绩" name="third">
        <div style="width: 100%">
          <el-table :data="tableData" stripe style="width: 100%">
            <el-table-column prop="tiku" label="关联题库" width="180" />
            <el-table-column prop="name" label="试卷名称" width="180" />
            <el-table-column prop="time" label="考试时间" />
            <el-table-column prop="pf" label="评分时间" />
            <el-table-column prop="cj" label="成绩" />
            <el-table-column prop="" label="操作" />
          </el-table>
        </div>
      </el-tab-pane>
    </el-tabs>
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
