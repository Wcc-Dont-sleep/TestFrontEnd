<template>
    <el-menu
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#e8e8f7"
      
      active-text-color="#4154f1"
      :collapse="isCollapse"
      :default-openeds="openeds"
      router
      >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span color="#012970">课程练习</span>
        </template>
        
        <el-menu-item-group   class="menu-item-group"  >
          <el-menu-item index="/triangle">(程序题)第1、9题:判断三角形</el-menu-item>
          <el-menu-item index="/calendar">(程序题)第2、10、11题:万年历问题</el-menu-item>
          <el-menu-item index="/sales">(程序题)第4题:电脑销售系统</el-menu-item>
          <el-menu-item index="/cash">(程序题)第7题:电信收费问题</el-menu-item>
          <el-menu-item index="/atm">(程序题)第12、15题:ATM</el-menu-item>
           <el-menu-item index="/sale">(程序题)第17题:销售系统</el-menu-item>
          
          <!-- <el-menu-item index="/nine">第15题:ATM机</el-menu-item> -->
         
         
          
        </el-menu-item-group>
      </el-submenu>
      <!-- <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item> -->
    </el-menu>
</template>

<script>

export default {
  name: "AsideBar",
  components: {},
  props: ['is-collapse'],
  data() {
    return {
      openeds: ['1'],
    }
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {},
  methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
  },
};
</script>

<style scoped lang="less">
  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 320px;
    min-height: 400px;
  }
  .menu-item-group {
    
    background-color: #8183f7; /* 修改背景颜色 */
    background-color: #ffffff
  }

  .menu-item-group .el-menu-item {
    margin-bottom: 3px; /* 修改下方间距 */
    background-color: #c1c1f7 !important;
    color: #ffffff;
    font-weight: bold;
    font-size: 16px;
  }
</style>