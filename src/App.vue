<template>
  <div id="app">
    <h1>pet adoption & pet supplies </h1>
    <p><b>Contact</b>: Mr.Chavez 4961 Woodbridge Lane Southfield ksq6l911d9dc#thrubay.com</p>
    <p><b>Contact Us, We will show you more pictures</b></p>
<!--    <img src="./assets/logo.png">-->
    <Album/>
<!--    <VideoPlayer/>-->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
// import VideoPlayer from './components/VideoPlayer'
// import ShowIp from "./components/ShowIp";
import Album from "./components/Album";

export default {
  name: 'App',
  components: {
    Album,
    // ShowIp,
    // HelloWorld,
    // VideoPlayer
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
