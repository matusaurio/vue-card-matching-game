<template>
  <div class="home container">
    <Instructions/>
  </div>
</template>

<script>
// @ is an alias to /src
import Instructions from '@/components/Instructions'

export default {
  name: 'home',
  components: {
    Instructions,
  }
}
</script>

<style scoped>
.home {
  text-align: center;
}
</style>
