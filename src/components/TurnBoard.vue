<template>
  <div>
    <div>
      현재 : {{nowTurn}}
    </div>
    <br/>
    <div>
      남은 턴 : {{leftTurn}}
    </div>
  </div>
</template>

<script>
export default {
  name: "TurnBoard",
  props: ['nowTurn', 'leftTurn'],
}
</script>

<style scoped>
  #turn {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    grid-column: 3 / 4;
    grid-row: 1;
    border-style: inset;
    border-width: 2px;
    height: 245px;
  }
</style>