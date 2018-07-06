<template>
  <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
    <el-menu-item index="1">
      <nuxt-link to="/">Home</nuxt-link>
    </el-menu-item>
    <el-menu-item index="2">
      <nuxt-link to="/about">About</nuxt-link>
    </el-menu-item>
  </el-menu>
</template>

<script>
  export default {
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1'
      };
    }
  }
</script>

<style lang="scss" scoped>
  .el-menu-item {
    padding: 0;
    a {
      display: inline-block;
      text-decoration: none;
      padding: 0 10px;
    }
  }
</style>