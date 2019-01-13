<template>
  <div id="app">
    <Header />
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view/>
  </div>
</template>

<script>
import Header from '@/components/layout/Header';

export default {
  name: 'app',
  components: {
    Header
  }
}
</script>


<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-transform: uppercase;
  background-color: #f1f1f1;
  background-image: url('./assets/images/supercharge-logo.svg');
  background-repeat: no-repeat;
  background-size: contain;
  background-attachment: fixed;
  background-position: center;
}

.btn-red {
  background-color: #ff0000;
  color: #fff;
  padding: 15px;
  border: none;
  border-radius: 5px;
}
</style>
