<template>
  <div>

    <div>
      <h2>{{ message }}</h2>
      <p>My opinion of Vue is {{ vue_js }}</p>
    </div>

    <div v-if="showSongs" v-for="song in songs" :key="song" >
      <h4>{{ song.name }}</h4>
      <p>{{ song.album }}</p>
      <p>{{ song.genre }}</p>
      <img :src= song.url alt="album cover">
      <p>{{ emptyArrayMessage }}</p>
    </div>
    <div v-else>
      <p>{{ loadMessage }}</p>
    </div>

    <div>
      <button @click="alertFunction">Click Me One</button>

      <button @click="hideSongs">
        Click Me Two
        <span v-if="showSongs">Hide Songs</span>
        <span v-else>Show Songs</span>
      </button>

      <button>Click Me Three</button>
      <br><br>

      <input type="text" v-model="alerting">
    </div>

    <!-- <div v-show="showSongs"></div> -->

  </div>
</template>

<script>
import FirstName from "./components/FirstName.vue";
import MyHobbies from "./components/MyHobbies.vue";
import Song from "./components/Song.vue";
import FavCodingLanguage from "./components/FavCodingLanguage.vue";

export default {
  // name: 'App',
  components:{
    FirstName,
    MyHobbies,
    Song,
    FavCodingLanguage,
  },
  data(){
    return{
      showSongs: true,
      alerting: '',
      message: 'I am amazing.',
      loadMessage: '',
      emptyArrayMessage: '',
      vue_js: 'Vue.js is the easiest framework I have learned.',
      songs: [
        {
        name: 'Protect Ya Neck',
        album: 'Enter the Wu-Tang (36 Chambers)',
        genre: 'Hip Hop',
        url: 'https://i.postimg.cc/DZyjXHJZ/wutang.jpg',
      },
        {
        name: 'Enter Sandman',
        album: 'Metalica',
        genre: 'Heavy Metal',
        url: 'https://i.postimg.cc/k41jFsKy/entersandman.jpg',
      },
        {
        name: 'Bulls on Parade',
        album: 'Evil Empire',
        genre: 'Hard Rock',
        url: 'https://i.postimg.cc/m2FdCQDQ/bullsonparade.jpg',
      },
        {
        name: 'Stay with Me',
        album: 'Pocket Park',
        genre: 'City Pop',
        url: 'https://i.postimg.cc/D0SxCGc3/staywithme.jpg',
      },
        {
        name: 'Cult of Personality',
        album: 'Vivid',
        genre: 'Classic Rock',
        url: 'https://i.postimg.cc/jq1gD8sx/cultofpersonality.jpg',
      },
    ]
    }
  },
  methods:{
    hideSongs(){
      this.showSongs = !this.showSongs;
      this.loadMessage = 'Loading...';
    },
    emptyArray(){
      if(!this.songs){
        this.emptyArrayMessage = 'There are no songs available.';
      }
    }
  },
  computed:{
    alertFunction(){
      alert(this.alerting);
    },

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img{
  width: 300px;
  height: 300px;
}
</style>
