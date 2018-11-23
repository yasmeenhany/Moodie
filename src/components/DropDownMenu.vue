<template>

  <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link">
    Dropdown List<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
    <el-dropdown-menu slot="dropdown">
      <el-dropdown-item command="stressed"> Stressed </el-dropdown-item>
      <el-dropdown-item> Depressed </el-dropdown-item>
      <el-dropdown-item> In love </el-dropdown-item>
      <el-dropdown-item> Heartbroken </el-dropdown-item>
      <el-dropdown-item> Unmotivated </el-dropdown-item>
       <el-dropdown-item> Bored </el-dropdown-item>
        <el-dropdown-item> Lonely </el-dropdown-item>
         <el-dropdown-item> Curious </el-dropdown-item>
          <el-dropdown-item> 3atef </el-dropdown-item>
           <el-dropdown-item> Abla Kamel </el-dropdown-item>
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
