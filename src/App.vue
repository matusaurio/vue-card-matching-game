<template>
  <div id="app">
    <Header />
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
html {
	box-sizing: border-box;
}

*,
*::before,
*::after {
	box-sizing: inherit;
}

html,
body {
	width: 100%;
	height: 100%;
	margin: 0;
	padding: 0;
}

body {
	background: #ffffff;
	font-family: 'Permanent Marker', cursive;
	font-size: 16px;
}

.container {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
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

.sm-txt {
  font-size: .7em;
  text-align: justify;
}
</style>
