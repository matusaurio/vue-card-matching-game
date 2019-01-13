<template>
  <div class="cards-container">
      <div 
        class="card"
        v-for="card in cards" 
        :key="card.id" 
        :class="{ card_reversed: !card.reversed }"
        @click="showCard(card)"
      >
        {{card.face.name}}
      </div>
    </div>
</template>

<script>
export default {
  name: 'Card',
  data() {
    return {}
  },
  mounted() {
    this.initializeCards();
  },
  props: ['cards', 'options','number', 'guesses'],
  methods: {
    initializeCards() {
      this.options = this.options.slice(0,this.number);
      for (let i = 0; i <= (this.options.length*2)-1; i++) {        
        this.cards.push({
          id:i,
          reversed: false,
          matched: false,
          face: this.assignCard()
        });
      }
      return this.cards;
    },
    showCard(card) {
      if (card.matched === true || !this.verifyDuplicate(card)) {
        return
      }
      this.$emit('compare-cards', card);
      // card.reversed = true;

      // setTimeout(() => {
      //   card.reversed = false
      // }, 2000);
    },
    verifyDuplicate(card) {
      if (this.guesses.length === 1 && this.guesses[0].id === card.id) {
        return false;
      }
      return true;
    },
    assignCard() {
      let pairs = this.options.filter(obj => obj.pairs >= 1);
      pairs = this.shuffleCards(pairs);
      let card = pairs[Math.floor(Math.random() * pairs.length)];
      this.decrease(card);
      return card;
    },
    shuffleCards(array) {
      var currentIndex = array.length, temporaryValue, randomIndex;

      // While there remain elements to shuffle...
      while (0 !== currentIndex) {

        // Pick a remaining element...
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex -= 1;

        // And swap it with the current element.
        temporaryValue = array[currentIndex];
        array[currentIndex] = array[randomIndex];
        array[randomIndex] = temporaryValue;
      }

      return array;
    },
    decrease(card) {      
      let item = this.options.find(obj => obj.name === card.name);
      return this.options[item.pairs-=1];
    },
  },
  watch: {
    cards: function(v) {
      if (v.length == 0) {
        this.initializeCards();
      }
    }
  }
}
</script>

<style>
.cards-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(5,100px);
  grid-gap: 10px;
  margin-left: 35%;
}

.card {
  background-color: #444;
  color: #fff;
  border-radius: 5px;
  padding: 20px;
  order: 1;
  cursor: pointer;
  box-shadow: 2px 2px #eee;
  transition: all .4s ease;
}

.card_reversed {
  background: #000;
  transform: rotateY(180deg);
}
</style>
