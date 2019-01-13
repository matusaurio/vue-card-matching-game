<template>
  <header class="header">
    <router-link to="/">
      <img src="../../assets/images/supercharge-logo.svg" alt="Supercharge Logo">
      <span>&nbsp; MEMORY GAME</span>
    </router-link>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  padding: 10px;
  display: flex;
  align-content: center;
}
.header img {
  height: 30px;
}
.header a {
  text-decoration: none;
  color: #fff;
}
</style>
