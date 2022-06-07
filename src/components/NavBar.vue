<template lang="html">

  <section class="nav-bar">
    <div id="navigator">
      <button id="reset" @click="restart()"> New colors</button>
      <span class="msg">{{ message }} </span>
      <button id="easy" :class="!isHard && 'selected'" @click="setDifficulty({ isHard: false, qty: 3 })">easy</button>
      <button id="hard" :class="isHard && 'selected'" @click="setDifficulty({ isHard: true, qty: 6 })">hard</button>
    </div>

  </section>

</template>

<script lang="js">

export default {
  name: 'nav-bar',
  props: ['message'],
  data() {
    return {
      // gameInfo: {
      isHard: false,
      squareQty: 0,
      colors: [],
      pickedColor: '',
      // }
    }
  },
  methods: {
    emit() {
      this.$emit('isHard', this.isHard);
      this.$emit('squareQty', this.squareQty);
    },
    setDifficulty({ isHard, qty }) {
      this.isHard = isHard;
      this.squareQty = qty;
      this.emit();
      this.init(qty);

      // this.restart();
    },
    init(qty) {
      this.colors = this.createNewColors(qty);
      this.pickedColor = this.colors[this.pickColor()];
      this.$emit('colors', this.colors);
      this.$emit('pickedColor', this.pickedColor);
      // this.restart();
    },
    createNewColors(numbers) {
      const arr = [];
      for (let i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
    },

    createRandomStringColor() {
      const newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")";
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    pickColor() {
      let quantity;
      if (this.isHard) {
        quantity = 6;
      } else {
        quantity = 3;
      }
      return Math.floor(Math.random() * quantity);
    },
    restart() {
      // this.colors = [];
      this.colors = this.createNewColors(this.squareQty);
      this.$emit('colors', this.colors);
      // pickedColor = this.colors[this.pickColor()];
      // colorDisplay.textContent = pickedColor;
      // this.textContent = "Pick New Colors!";
      // header.style.backgroundColor = "steelblue";
      // messageDisplay.textContent = "";
      // restartButton.textContent = "New Colors!";
      // for (var i = 0; i < squares.length; i++) {
      //   squares[i].style.backgroundColor = colors[i];
      // }
    }
  },
  computed: {

  }
}


</script>

<style scoped lang="css">
#navigator {

  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;

}

.msg {
  color: red;
  display: inline-block;
  width: 20%;
}

button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}

button:hover {
  color: white;
  background-color: steelblue;
}

.selected {
  background-color: steelblue;
  color: white;
}
</style>
