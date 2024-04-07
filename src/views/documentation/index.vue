<template>
  <div class="app-container documentation-container">
    <div style="width: 100%">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="">
          <el-select v-model="formInline.region" placeholder="选择考试状态">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
        </el-form-item>
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
    <div style="width: 100%;">
      <el-card class="card testCard">
        <h3>路由交换测试</h3>
        <el-timeline :reverse="reverse">
          <el-timeline-item
            v-for="(activity, index) in activities"
            :key="index"
            :timestamp="activity.timestamp"
          >
            {{ activity.content }}
          </el-timeline-item>
        </el-timeline>
        <p>所属题库：路由交换第一卷实验</p>
        <p>关联学期：23级第二学期</p>
        <div>
          <el-button round type="primary" class="button">已结束</el-button>
          <el-button round type="text" class="button">尚未提交试卷</el-button>

        </div>
 
      </el-card>
      <el-card class="card testCard">
        <h3>路由交换测试</h3>
        <el-timeline :reverse="reverse">
          <el-timeline-item
            v-for="(activity, index) in activities"
            :key="index"
            :timestamp="activity.timestamp"
          >
            {{ activity.content }}
          </el-timeline-item>
        </el-timeline>
        <p>所属题库：路由交换第一卷实验</p>
        <p>关联学期：23级第二学期</p>
        <div>
          <el-button round type="primary" class="button">已结束</el-button>
          <el-button round type="text" class="button">尚未提交试卷</el-button>

        </div>
 
      </el-card>
      <el-card class="card testCard">
        <h3>路由交换测试</h3>
        <el-timeline :reverse="reverse">
          <el-timeline-item
            v-for="(activity, index) in activities"
            :key="index"
            :timestamp="activity.timestamp"
          >
            {{ activity.content }}
          </el-timeline-item>
        </el-timeline>
        <p>所属题库：路由交换第一卷实验</p>
        <p>关联学期：23级第二学期</p>
        <div>
          <el-button round type="primary" class="button">已结束</el-button>
          <el-button round type="text" class="button">尚未提交试卷</el-button>

        </div>
 
      </el-card>
    </div>
  </div>
</template>

<script>
// import DropdownMenu from '@/components/Share/DropdownMenu'

export default {
  name: "Documentation",
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
