<template>
  <div class="instructions">
    <h1>SUPERCHARGE</h1>
    <h4>Memory Game</h4>
    <br>
    <!-- <ul>
      <li>When the user clicks a card, “flip it over” and reveal the hidden image.</li>
      <li>When two cards are revealed:
        <ul>
          <li>If the cards are identical, remove them from play.</li>
          <li>If they are not, flip them back.</li>
        </ul>
      </li>
      <li>The game ends when all cards are removed.</li>
    </ul> -->
    <br>
    <form @submit.prevent="startGame">
      <label for="number_cards">Deck size:</label> <br>
      <select name="number_cards" v-model="number">
        <option value="6" selected>6</option>
        <option value="8">8</option>
        <option value="10">10</option>
        <option value="12">12</option>
        <option value="14">14</option>
        <option value="16">16</option>
        <option value="18">18</option>
        <option value="20">20</option>
      </select> <br>
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
}

label {
  font-size: 8px;
}
select {
  margin-bottom: 15px;
}
input {
  margin-bottom: 15px;
  text-transform: uppercase;
}
</style>
