<template>

  <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link">
    Dropdown List<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
    <el-dropdown-menu slot="dropdown">
      <el-dropdown-item command="XR7pSHJFdfe4gfbzxp8H"> Stressed </el-dropdown-item>
      <el-dropdown-item command="k2IksT9Dfb5Q0h4OPe16"> Depressed </el-dropdown-item>
      <el-dropdown-item command="4FE1T7lrMW6UyUsUCUmE"> In love </el-dropdown-item>
      <el-dropdown-item command="dtD164sRvLbcQs85izyq"> Heartbroken </el-dropdown-item>
      <el-dropdown-item command="IjA6UlcVPGy5I3krrDO3"> Unmotivated </el-dropdown-item>
      <el-dropdown-item command="a0mZvFLsgATyNGTFgY2t"> Bored </el-dropdown-item>
      <el-dropdown-item command="fapcdbEEJP7ugsZktMW6"> Lonely </el-dropdown-item>
      <el-dropdown-item command="3gg0uKKvOxAmjp2LdxZ0"> Curious </el-dropdown-item>
      <el-dropdown-item command="mGwBIbWS1m0crGc5mjoJ"> 3atef </el-dropdown-item>
      <el-dropdown-item command="hwtfEJrET5UrzVx1Td7N"> Abla Kamel </el-dropdown-item>
    </el-dropdown-menu>
  </el-dropdown>

</template>

<script>
  import firebase from 'firebase';
  var config = {
    apiKey: "AIzaSyBTeATU2uLFj34RPEtmHlnNxyC72w7RGm8",
    authDomain: "moodie-6f977.firebaseapp.com",
    databaseURL: "https://moodie-6f977.firebaseio.com",
    projectId: "moodie-6f977",
    storageBucket: "moodie-6f977.appspot.com",
    messagingSenderId: "437544356268"
  };
  firebase.initializeApp(config);
  var db = firebase.firestore();
  db.settings({
    timestampsInSnapshots: true
  });
  export default{
      methods: {
          moodSelected(command){
          var docRef = db.collection("mood-genre").doc(command);

      docRef.get().then(function(doc) {
          if (doc.exists) {
              console.log("Document data:", doc.data());
          } else {
              // doc.data() will be undefined in this case
              console.log("No such document!");
          }
      }).catch(function(error) {
          console.log("Error getting document:", error);
      });
          },
      getGenre() {

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
