<template>
  <div class="admin-container">
    <el-container>
      <!-- 左侧菜单栏 -->
      <el-aside with="auto">
        <!-- 预留存放logo的位置 -->
        <div class="logo"></div>
        <!-- 菜单栏 -->
        <app-aside :isCollapse="isCollapse"></app-aside>
      </el-aside>
      <!-- 右侧内容 -->
      <el-container>
        <!-- 头部 -->
        <el-header>
          <app-header @onChange="changeCollapse"></app-header>
        </el-header>
        <!-- 主体 -->
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>
<script>
  // 引入组件
  import Aside from "../components/Aside";
  import Header from "../components/Header";
  
  export default {
    name: "admin-index",
    data() {
      return {
        isCollapse: false
      };
    },
    // 注册组件
    components: {
      "app-aside": Aside,
      "app-header": Header
    },
    methods: {
      changeCollapse() {
        this.isCollapse = !this.isCollapse;
      }
    }
  };
</script>


<style>
  .admin-container {
    position: fixed;
    width: 100%;
    top: 0;
    bottom: 0;
  }
  
  .el-header {
    color: #333;
  }
  
  .el-aside {
    display: flex;
    flex-direction: column;
  }
  
  .el-main {
    background-color: #e9eef3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  
  .el-container {
    margin-bottom: 40px;
    /*继承admin-container的高度*/
    height: 100%;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
  
  .logo {
    height: 60px;
    background: #454f5a;
  }
</style>