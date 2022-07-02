<template>
  <div class="background" @submit.prevent>
    <div class="container">
    <div>
      <input type="text" v-model="input" :disabled="input"/>
    </div>
      <div class="keypad">
        <button class="highlight" @click="clear" id="clear">Clear</button>
        <button class="highlight" @click="oneClear" id="backspace">C</button>
        <button class="highlight" name="/" @click="handleClick">&divide;</button>
        <button name="7" @click="handleClick">7</button>
        <button name="8" @click="handleClick">8</button>
        <button name="9" @click="handleClick">9</button>
        <button class="highlight" name="*" @click="handleClick">&times;</button>
        <button name="4" @click="handleClick">4</button>
        <button name="5" @click="handleClick">5</button>
        <button name="6" @click="handleClick">6</button>
        <button class="highlight" name="-" @click="handleClick">-</button>
        <button name="1" @click="handleClick">1</button>
        <button name="2" @click="handleClick">2</button>
        <button name="3" @click="handleClick">3</button>
        <button class="highlight" name="+" @click="handleClick">+</button>
        <button name="0" @click="handleClick">0</button>
        <button name="." @click="handleClick">.</button>
        <button class="highlight" @click="calculate" id="result">=</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return{
      input: "",
    }
  },
  methods: {
    calculate () {
      try{
        this.input = eval(this.input).toString()
      } catch{
        this.input = "Error"
      }

    },
    handleClick (e) {
      this.input = this.input.concat(e.target.name)
    },
    clear () {
      this.input = ""
    },
    oneClear () {
      this.input = this.input.slice(0, -1)
    },
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  font-family: "Roboto", sans-serif;
  font-size: 18px;

}
.background {
  display: flex;
  height: 100vh;
  background-color: #448EF6;
}
.container {
  top: 50%;
  left: 50%;
  position: absolute;
  transform: translate(-50%, -50%);
  background-color: black;
  padding: 15px;
  border-radius: 5px;
}
.keypad {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(60px, auto);
}
input {
  background-color: black;
  color: white;
}
input[type="text"] {
  height: 75px;
  width: 249px;
  background-color: #10111600;
  border: 0px;
  color: #ffffff;
  text-align: right;
  font-size: 25px;
  font-weight: 500;
  letter-spacing: 1px;
}
input:focus,
input:active,
button:focus,
button:active {
  outline: none;
}

.highlight {
  background-color: #448EF6;
  color: black;
  transition: 0.1s ease-in;
}

.highlight:hover {
  background-color: #4478F6;
}
button {
  margin: 5px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background: #262834;
  color: #fff;
  font-weight: 500;
}
#clear {
  grid-column: 1/3;
  grid-row: 1;
  color: #262834;
}
#result {
  grid-column: 3/5;
  grid-row: 5;
}

#backspace {
  color: #262834;
}
</style>
