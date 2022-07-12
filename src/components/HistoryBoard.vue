<template>
  <div>
    <p style="font-size: 25px">History</p>
    <div id="historyContent">
      <p v-for="(item,index) in this.historyArr" v-bind:key="index">{{item}}</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: "HistoryBoard",
    props: ['historyArr'],
  }
</script>

<style scoped>
  #history{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    grid-column: 3 / 4;
    grid-row: 2;
    border-style: inset;
    border-width: 2px;
    height: 250px;
  }
  #historyContent{
    width: 90%;
    text-align: center;
    overflow-y: auto;
  }
</style>