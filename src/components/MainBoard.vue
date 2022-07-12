<template>
  <div>
    <input v-if="inputState" v-model="inputNum" style="margin-bottom: 10px"/>
    <button v-if="inputState" @click="turnProcess">입력</button>
    <p v-if="result === 'up'">👍</p>
    <p v-else-if="result === 'down'">👎</p>
    <p v-else-if="result === 'target'" style="font-size: 50px">👏</p>
    <p v-else-if="result === 'fail'">ㅠㅠ</p>
    <p v-else> </p>
  </div>
</template>

<script>

export default {
  name: "MainBoard",
  props: ['nowTurn', 'leftTurn', 'target', 'inputState'],
  data() {
    return{
      input_state: this.inputState,
      inputNum: null,
      PropsNowTurn: this.nowTurn,
      PropsLeftTurn: this.leftTurn,
      result: null,
    }
  },
  methods: {
    turnProcess: function() {
      this.$emit('change-num-function', this.inputNum);
      this.$emit('turnProcess');
      this.$emit('addHistory');
      if(this.inputNum > this.target){
        this.result = 'down';
      } else if(this.inputNum < this.target){
        this.result = 'up';
      } else{
        this.result = 'target';
        alert('👏정답!!👏');
        this.input_state = false;
        this.$emit('clickStart');
      }
      if(this.nowTurn === 9){
        this.input_state = false;
        this.result = 'fail';
        this.$emit('clickStart');
      }
      this.inputNum = null;
    }
  }
}
</script>

<style scoped>
  #main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    grid-column: 1 / 3;
    grid-row: 1 / 3;
    border-style: inset;
    border-width: 2px;
    height: 500px;
  }
</style>