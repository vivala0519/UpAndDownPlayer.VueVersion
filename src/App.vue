<template>
  <h2>10턴 안에 숫자를 맞혀라</h2>
  <button v-if="!start" @click="clickStart">{{ buttonName }}</button>
  <div v-if="view" id="wrapper">
    <MainBoard id="main" :inputState="inputState" v-on:addHistory="addHistory" v-on:turnProcess="turnProcess" v-on:clickStart="clickStart" :nowTurn="nowTurn" :leftTurn="leftTurn" :target="target" @change-num-function="changeNum"/>
    <TurnBoard id="turn" :nowTurn="nowTurn" :leftTurn="leftTurn"/>
    <HistoryBoard id="history" :historyArr="historyArr"/>
  </div>
</template>

<script>
import MainBoard from "@/components/MainBoard";
import HistoryBoard from "@/components/HistoryBoard";
import TurnBoard from "@/components/TurnBoard";

export default {
  name: 'App',
  data() {
    return {
      start: false,
      view: false,
      buttonName: '시작하기',
      nowTurn: 0,
      leftTurn: 10,
      target: Math.floor(Math.random() * 100) + 1,
      NumState: 0,
      historyArr: [],
      inputState: true,
    }
  },
  methods: {
    clickStart: function() {
      console.log('click start')
      if(this.start === false){
        this.start = true;
        this.view = true;
        this.buttonName = '다시 시작';
        this.inputState = true;
      } else{
        this.start = false;
        this.historyArr = [];
        this.nowTurn = 0;
        this.leftTurn = 10;
        this.inputState = true;
      }
    },
    turnProcess: function() {
      if(this.nowTurn < 10){
        this.nowTurn ++;
        this.leftTurn --;
      }
    },
    changeNum(value) {
      this.NumState = value;
    },
    addHistory: function() {
      this.historyArr.push(this.NumState);
    }
  },
  components: {
    MainBoard, TurnBoard, HistoryBoard,
  },
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  #wrapper {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    border-style: inset;
    border-width: 2px;
    width: 1000px;
    margin: auto;
  }
</style>
