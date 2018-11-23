<template>

  <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link">
    Dropdown List<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
    <el-dropdown-menu slot="dropdown">
      <el-dropdown-item command="stressed"> Stressed </el-dropdown-item>
      <el-dropdown-item command="depressed"> Depressed </el-dropdown-item>
      <el-dropdown-item command="inLove"> In love </el-dropdown-item>
      <el-dropdown-item command="heartbroken"> Heartbroken </el-dropdown-item>
      <el-dropdown-item command="unmotivated"> Unmotivated </el-dropdown-item>
       <el-dropdown-item command="bored"> Bored </el-dropdown-item>
        <el-dropdown-item command="lonely"> Lonely </el-dropdown-item>
         <el-dropdown-item command="curious"> Curious </el-dropdown-item>
          <el-dropdown-item command="3atef"> 3atef </el-dropdown-item>
           <el-dropdown-item command="ablaKamel"> Abla Kamel </el-dropdown-item>
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
