<template>
  <div style="height: 100%" ref="tabs">
    <el-card shadow="hover">
      <el-tabs v-model="activeName">
        <el-tab-pane label="问题描述与分析" name="first">
          <Question />
        </el-tab-pane>

        <el-tab-pane label="测试用例输入" name="second">
          <SystemTest :parentHeight="parentHeight" />
        </el-tab-pane>


        
      </el-tabs>
    </el-card>
  </div>
</template>

<script>
import Question from "./question";
import SystemTest from "./systemtest";
import SingleCase from "./singlecase";
import ExcelFile from "./excelfile";
import BugRecord from "./bug";

export default {
  name: "Money",
  components: {
    Question,
    SystemTest,
    SingleCase,
    ExcelFile,
    BugRecord
  },
  props: {},
  data() {
    return {
      activeName: "first",
      parentHeight: 3333,
    };
  },
  computed: {},
  watch: {},
  created() {
    window.addEventListener("resize", this.getHeight);
  },
  mounted() {},
  methods: {
    getHeight() {
      try {
        this.parentHeight = this.$refs.tabs.offsetHeight;
      } catch (err) {}
    },
  },
};
</script>

<style scoped lang="less">
</style>