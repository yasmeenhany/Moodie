<template>

  <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link">
    Choose a Mood<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
    <el-dropdown-menu slot="dropdown">
      <el-dropdown-item command="stressed"> Stressed </el-dropdown-item>
      <el-dropdown-item command="depressed"> Depressed </el-dropdown-item>
      <el-dropdown-item command="inLove"> In love </el-dropdown-item>
      <el-dropdown-item command="heartBroken"> Heartbroken </el-dropdown-item>
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
  import firebase from 'firebase';
  import con from '../../config/config.json';
  import axios from 'axios';
  var config = {
    apiKey: con.apiKey,
    authDomain: con.authDomain,
    databaseURL: con.databaseURL,
    projectId: con.projectId,
    storageBucket: con.storageBucket,
    messagingSenderId: con.messagingSenderId
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
              console.log("Document data:", doc.data().genre);
              var url = con.apiBaseURL+ doc.data().genre.toString();
              console.log("URL", url)
            axios.get(url)
              .then(response => {
                console.log("Poster ", con.posterBaseURL+response.data.results[0].poster_path);

              })
              .catch(e => {
                // this.errors.push(e)
                console.log("error");
              })
          } else {
              // doc.data() will be undefined in this case
              console.log("No such document!");
          }
      }).catch(function(error) {
          console.log("Error getting document:", error);
      });
          },
        getGenre(url) {
          axios.get(url)
            .then(response => {
              // JSON responses are automatically parsed.
              //this.posts = response.data
              console.log("Response"+ response.data);
            })
            .catch(e => {
             // this.errors.push(e)
              console.log("error");
            })
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
