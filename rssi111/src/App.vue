<template>

  <div id="app">
    <img src="./assets/sendai.png" style="width:200px;height:200px;">
    <div>
      <h1>iBeaconReceive</h1>
    </div>
    <div class="page-header">
    </div>
    <h3> RSSI : </h3> <p v-for="value in RSSI">{{value.values}}</p>

    <h3> Latitude : </h3> <p v-for="value in Lat">{{value.values}}</p>

    <h3> Longtitude : </h3> <p v-for="value in Long">{{value.values}}</p>

    <!--<h3> DateTime : </h3> <p v-for="value in TimeDate">{{value.values}}</p>-->

  </div>

</template>

<script>

import Hello from './components/Hello'
import Firebase from 'firebase'

let config = {
  apiKey: "AIzaSyDqdodpFDQC597bdnTgu9bvVM1wQHSaH0I",
  authDomain: "rssi-to-web.firebaseapp.com",
  databaseURL: "https://rssi-to-web.firebaseio.com",
  projectId: "rssi-to-web",
  storageBucket: "rssi-to-web.appspot.com",
  messagingSenderId: "1037979345662"
}

let app = Firebase.initializeApp(config);
let db = app.database();

let rssiRef = db.ref('RSSI');
let latRef = db.ref('Lat');
let longRef = db.ref('Long');
let tdRef = db.ref('TimeDate');


export default {
  name: 'app',
  firebase: {
    RSSI: rssiRef,
    Lat: latRef,
    Long: longRef,
    TimeDate: tdRef
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
