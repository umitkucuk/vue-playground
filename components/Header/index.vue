<template>
  <el-menu :default-active="$route.path" mode="horizontal" router>
    <el-menu-item index="/">
      <nuxt-link to="/">Home</nuxt-link>
    </el-menu-item>
    <el-menu-item index="/about">
      <nuxt-link to="/about">About</nuxt-link>
    </el-menu-item>
    <el-menu-item index="/epics">
      <nuxt-link to="/epics">Epics</nuxt-link>
    </el-menu-item>
    <el-menu-item index="/sprints">
      <nuxt-link to="/sprints">Sprints</nuxt-link>
    </el-menu-item>
    <el-menu-item index="/app-sections">
      <nuxt-link to="/app-sections">App Sections</nuxt-link>
    </el-menu-item>
    <el-menu-item index="/salt-page">
      <nuxt-link to="/salt-page">Salt Examples</nuxt-link>
    </el-menu-item>
  </el-menu>
</template>

<script>
  export default {

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
