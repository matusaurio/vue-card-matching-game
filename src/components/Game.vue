<template>
  <div class="game">
    <div class="info">
      <div class="sm-txt">Current tries: {{ tries }}</div>
      <div class="sm-txt">Best: {{ best }}</div>
      <div class="col">
      <button @click="restartGame" class="btn">Restart</button>
      </div>
    </div>
    <div class="cards">
      <Card
        :cards="cards" 
        :options="options" 
        :number="number" 
        :guesses="guesses" 
        @compare-cards="sendToCompare"
      />
    </div>
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Game',
  components: {
    Card
  },
  props: ['number'],
  data() {
    return {
      cards: [],
      options: [
        {
          name: 'angular',
          path: '../assets/images/cards/angular.png',
          pairs: 2
        },
        {
          name: 'd3',
          path: '../assets/images/cards/d3.png',
          pairs: 2
        },
        {
          name: 'jenkins',
          path: '../assets/images/cards/jenkins.png',
          pairs: 2
        },
        {
          name: 'postcss',
          path: '../assets/images/cards/postcss.png',
          pairs: 2
        },
        {
          name: 'react',
          path: '../assets/images/cards/react.png',
          pairs: 2
        },
        {
          name: 'redux',
          path: '../assets/images/cards/redux.png',
          pairs: 2
        },
        {
          name: 'sass',
          path: '../assets/images/cards/sass.png',
          pairs: 2
        },
        {
          name: 'supercharge',
          path: '../assets/images/cards/supercharge.png',
          pairs: 2
        },
        {
          name: 'ts',
          path: '../assets/images/cards/ts.png',
          pairs: 2
        },
        {
          name: 'webpack',
          path: '../assets/images/cards/webpack.png',
          pairs: 2
        },
      ],
      tries: 0,
      count: 0,
      best: 0,
      guesses: [],
    }
  },
  methods: {
    sendToCompare(card) {
      card.reversed = !card.reversed;
      ++this.count;
      this.guesses.push(card);
      this.tries++;
      if (this.guesses.length > 1) {
        this.compareCards()
      }
    },
    compareCards() {
      if (this.guesses[0].face.name === this.guesses[1].face.name) {
        this.guesses[1].matched = true;
        this.guesses[0].matched = true;
        this.resetTries()
      } else {
        setTimeout(() => {
          this.resetTries()
        }, 500);
      }
    },
    resetTries() {
      this.count = 0;
      this.guesses = [];
      for (let i = 0; i < this.cards.length; i++) {
        let card = this.cards[i];
        if (card.reversed === true && card.matched === false) {
          this.cards[i].reversed =  false;
        }
      }
    },
    restartGame() {
      this.count = 0;
      this.options.forEach(e => e.pairs = 2);
      this.guesses = [];
      this.cards = [];
    }
  }
}
</script>

<style scoped>
.game {
  text-align: center;
}

.btn {
  background: #fff;
  border: 1px solid #333;
  border-radius: 5px;
  padding: 10px 25px;
  text-transform: uppercase;
}

.cards {
  margin-top: 25px;
  display: block;
  margin: auto;
}

.info {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  margin-top: 30px;
}
</style>
