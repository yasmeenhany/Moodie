<template >
  <div class="moodie">
    <el-dropdown @command="moodSelected">
  <span class="el-dropdown-link" v-if="selectedMood == null">
    Choose a Mood<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
      <span class="el-dropdown-link" v-if="selectedMood != null">
    {{selectedMood}}<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
      <el-dropdown-menu slot="dropdown" class="el-dropdown-item">
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
    <br>
    <br>
    <br>
    <div class="trinity-rings-spinner" v-if="loading">
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
    </div>
    <el-row >
      <el-col :span="4" v-for="movie in movies" :key="movie.title">
        <el-card :body-style="{ padding: '0px', height: '380px', color: '#ff3b3f', background: '#0f1626'}">
          <img :src="movie.poster" class="image">
          <div style="padding: 10px; align-content: center">
            <span>{{movie.title}}</span>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
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
    data() {
      return {
        selectedMood: null,
        loading: false,
        movies: [
//          {
//            poster: null,
//            title: null
//          }
        ]
      };
    },
    methods: {
      moodSelected(command){
          this.loading = true
        this.selectedMood = command.toUpperCase()
        var docRef = db.collection("mood-genre").doc(command);
        self = this
        docRef.get().then(function(doc) {
          if (doc.exists) {
            console.log("mood: ", command);
            console.log("Document data:", doc.data().genre);
            var url = con.apiBaseURL+ doc.data().genre.toString();
            console.log("URL", url)
            self.getFromAPI(url)
          } else {
            // doc.data() will be undefined in this case
            console.log("No such document!");
          }
        }).catch(function(error) {
          console.log("Error getting document:", error);
        });
      },
      getFromAPI(url) {
        axios.get(url)
          .then(response => {
              this.loading = false;
            this.movies = response.data.results;
            var i =0;
            console.log("movies from 3andi"+ this.movies)
            for(i =0; i< this.movies.length; i++){
              this.movies[i].poster= con.posterBaseURL+response.data.results[i].poster_path
              this.movies[i].title= response.data.results[i].original_title
              console.log(this.movies[i]);
            }

          })
          .catch(e => {
            // this.errors.push(e)
            console.log(e.message);
          })
      }

    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .moodie {
    font-family: Helvetica;
    font-weight: bold;
    padding: 15px;
  }
  .el-dropdown-link {
    cursor: pointer;
    color: #ff3b3f;
    padding-top: 10px;
  }
  .el-dropdown-item {
    font-family: Helvetica;
    background-color: #0f1626;
    color: #ff3b3f;
  }
  .el-icon-arrow-down {
    font-size: 12px;
    color: #ff3b3f;
  }


  .image {
    width: 100%;
    display: block;
  }

  .trinity-rings-spinner, .trinity-rings-spinner * {
    box-sizing: border-box;
    align-content: center;
  }

  .trinity-rings-spinner {
    height: 66px;
    width: 66px;
    padding: 3px;
    position: relative;
    left: 50%;
    top: 30%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    overflow: hidden;
    box-sizing: border-box;
  }
  .trinity-rings-spinner .circle {
    position: absolute;
    display:block;
    border-radius:50%;
    border: 3px solid #ff3b3f;
    opacity: 1;
  }

  .trinity-rings-spinner .circle:nth-child(1) {
    height: 60px;
    width: 60px;
    animation : trinity-rings-spinner-circle1-animation 1.5s infinite linear;
    border-width: 3px;
  }
  .trinity-rings-spinner .circle:nth-child(2) {
    height: calc(60px * 0.65);
    width: calc(60px * 0.65);
    animation : trinity-rings-spinner-circle2-animation 1.5s infinite linear;
    border-width: 2px;
  }
  .trinity-rings-spinner .circle:nth-child(3) {
    height: calc(60px * 0.1);
    width: calc(60px * 0.1);
    animation:trinity-rings-spinner-circle3-animation 1.5s infinite linear;
    border-width: 1px;
  }

  @keyframes trinity-rings-spinner-circle1-animation{
    0% {
      transform: rotateZ(20deg) rotateY(0deg);
    }
    100% {
      transform: rotateZ(100deg) rotateY(360deg);
    }
  }
  @keyframes trinity-rings-spinner-circle2-animation{
    0% {
      transform: rotateZ(100deg) rotateX(0deg);
    }
    100% {
      transform: rotateZ(0deg) rotateX(360deg);
    }
  }
  @keyframes trinity-rings-spinner-circle3-animation{
    0% {
      transform: rotateZ(100deg) rotateX(-360deg);
    }
    100% {
      transform: rotateZ(-360deg) rotateX(360deg);
    }
  }

</style>
