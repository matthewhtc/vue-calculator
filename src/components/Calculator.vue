<template>
  <div class='calculator'>
    <div class='display'>
      <div class='miniDisplay'>{{ previous || '0' }}</div>
      {{ current || '0' }}</div>
    <div @click='clear' class='btn'>C</div>
    <div @click='sign' class='btn'>+/-</div>
    <div @click='percent' class='btn'>%</div>
    <div @click='operation("/")' class='btn operator'>÷</div>
    <div @click='append("7")' class='btn'>7</div>
    <div @click='append("8")' class='btn'>8</div>
    <div @click='append("9")' class='btn'>9</div>
    <div @click='operation("×")' class='btn operator'>×</div>
    <div @click='append("4")' class='btn'>4</div>
    <div @click='append("5")' class='btn'>5</div>
    <div @click='append("6")' class='btn'>6</div>
    <div @click='operation("-")' class='btn operator'>-</div>
    <div @click='append("1")' class='btn'>1</div>
    <div @click='append("2")' class='btn'>2</div>
    <div @click='append("3")' class='btn'>3</div>
    <div @click='operation("+")' class='btn operator'>+</div>
    <div @click='append("0")' class='zero btn' style='border-radius: 0 0 0 5px'>0</div>
    <div @click='dot' class='btn'>.</div>
    <div @click='equal' class='btn operator' style='border-radius: 0 0 5px 0'>=</div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      previous: '',
      current: '',
      operator: null,
      operatorClicked: false
    }
  },
  methods: {
    clear() {
      this.current = '';
      this.operatorClicked = false;
      this.operator = null;
      this.previous = '';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? 
        this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.previous = `${this.previous}${number}`
      this.current = `${this.current}${number}`
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        if (!this.current.length) {
          this.append('0');
        }
        this.append('.');
      } 
    },
    setPrevious() {
      this.operatorClicked = true;
    },
    operation(sign) {
      if (this.previous.indexOf('=') !== -1) {
        this.previous = this.current;
      }
      if (!this.operatorClicked) {
        this.current = `${this.current}${sign}`;
        this.previous = `${this.previous}${sign}`;
        this.setPrevious();
      }
    },
    equal() {
      this.current = `${eval(this.previous.replace('×', '*'))}`;
      this.previous = `${this.previous}=${eval(this.previous.replace('×', '*'))}`;
      this.operatorClicked = false;
    }
  }
}
</script>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto');
$orange: #FF5722;
$blue-grey: #607D8B;

.calculator {
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
  width: 350px;
  margin: 0 auto;
  font-size: 25px;
  display: grid;
  grid-template-columns: repeat(4, 1fr); // 4 x infinity grid
  grid-auto-rows: minmax(65px, auto); // 50 px in height
  border-radius: 5px;
  margin: 30px auto 30px;

  .display, .miniDisplay {
    grid-column: 1 / 5; // start at column 1, end after column 4
    background-color: #FFFFFF;
    color: #212121;
    padding: 10px;
    text-align: right;
    font-size: 25px;
  }

  .miniDisplay {
    font-size: 20px;
    padding: 0;
    height: auto;
  }

  .display {
    border-radius: 5px 5px 0 0;
  }

  .zero {
    grid-column: 1 / 3;
  }

  .btn {
      background-color: $blue-grey;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
    }

  .btn:hover {
    cursor: pointer;
    background-color: darken($blue-grey, 10%);
  }

  .operator {
    background-color: $orange;
    color: white;
  }

  .operator:hover {
    background-color: darken($orange, 10%);
  }
}
</style>
