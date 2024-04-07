<template>
  <div class="app-container documentation-container">
    <div style="width: 100%">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="">
          <el-select v-model="formInline.region" placeholder="选择学期">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="">
          <el-input v-model="formInline.user" placeholder="试卷名称"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">搜索</el-button>
        </el-form-item>
      </el-form>
    </div>
    <el-tabs style="width: 100%" v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="实验报告" name="first"></el-tab-pane>
      <el-tab-pane label="实验测评" name="second"></el-tab-pane>
      <el-tab-pane label="考试成绩" name="third">
        <div style="width: 100%">
          <el-table :data="tableData" stripe style="width: 100%">
            <el-table-column prop="date" label="关联题库" width="180">
            </el-table-column>
            <el-table-column prop="name" label="试卷名称" width="180">
            </el-table-column>
            <el-table-column prop="address" label="考试时间"> </el-table-column>
            <el-table-column prop="address" label="评分时间"> </el-table-column>
            <el-table-column prop="address" label="成绩"> </el-table-column>
            <el-table-column prop="address" label="操作"> </el-table-column>
          </el-table>
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
// import DropdownMenu from '@/components/Share/DropdownMenu'

export default {
  name: "Guide",
  // components: { DropdownMenu },
  data() {
    return {
      formInline: {
        user: "",
        region: "",
      },
      reverse: false,
      activities: [
        {
          content: "",
          timestamp: "2018-04-15",
        },
        {
          content: "",
          timestamp: "2018-04-16",
        },
      ],
    };
  },
  methods: {
    onSubmit() {
      console.log("submit!");
    },
  },
};
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
