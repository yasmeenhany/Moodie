<template>

  <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link">
    Dropdown List<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
    <el-dropdown-menu slot="dropdown">
      <el-dropdown-item command="hi">Action 1</el-dropdown-item>
      <el-dropdown-item>Action 2</el-dropdown-item>
      <el-dropdown-item>Action 3</el-dropdown-item>
      <el-dropdown-item >Action 4</el-dropdown-item>
      <el-dropdown-item >Action 5</el-dropdown-item>
    </el-dropdown-menu>
  </el-dropdown>

</template>

<script>
  export default{
      methods: {
          moodSelected(command){
              console.log(command)
          }
      }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-dropdown-link {
    cursor: pointer;
    color: #409EFF;
  }
  .el-icon-arrow-down {
    font-size: 12px;
  }
</style>
