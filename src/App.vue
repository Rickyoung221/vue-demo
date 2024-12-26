<template>
  <div class="common-layout">
    <el-container>
      <el-header>Header</el-header>
      <el-main>
        <h1>Hello, World</h1>
        <!-- 确保组件正常使用 -->
        <SnakeGame />
        <el-button type="primary">Button</el-button>
        <el-input v-model="message" placeholder="Please type" />
        <p>The content you enter: {{ message }}</p>
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
import SnakeGame from "./components/SnakeGame.vue"; // 导入组件

export default {
  components: {
    SnakeGame, // 注册组件
  },
  data() {
    return {
      message: "", // 定义绑定数据
    };
  },
};
</script>

<style>
.common-layout {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, sans-serif;
}

el-container {
  height: 100vh;
}

el-header,
el-footer {
  background-color: #b3c0d1;
  text-align: center;
  line-height: 60px;
}

el-main {
  padding: 20px;
  text-align: center;
}
</style>
