<template>
  <div id="instructions">
    <h1>SUPERCHARGE</h1>
    <h2>Memory Game</h2>
    <form @submit.prevent="startGame">
      <label for="number_cards">Deck size:</label>
      <input type="number" v-model="number" name="number">
      <!-- <select name="number_cards">
        <option value="6">6</option>
        <option value="8">8</option>
        <option value="10">10</option>
        <option value="12">12</option>
        <option value="14">14</option>
        <option value="16">16</option>
        <option value="18">18</option>
        <option value="20">20</option>
      </select> -->
      <input type="submit" value="Start New Game" class="btn-red">
    </form>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  data() {
    return {
      number: 0
    }
  },
  methods: {
    startGame(number) {
      const newGame = {
        number: this.number,
      }
      this.$router.push({
        name: 'Game',
        params: newGame
      });
    }
  }
}
</script>

<style scoped>
.instructions {
  text-align: center;
}
</style>
