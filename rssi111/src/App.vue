<template>
  <div id="app">
    <img src="./assets/logo.png">

      <p v-for="mes in message">
        {{ mes.values }}
      </p>

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

let messageRef = db.ref('message');

export default {
  name: 'app',
  firebase: {
    message: messageRef
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
