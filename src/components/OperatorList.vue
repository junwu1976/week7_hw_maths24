<template>
  <div>
      <h1>Operator List</h1>
      <ul>
          <li>+</li>
          <li>-</li>
          <li>x</li>
          <li>&divide</li>
          <li>(</li>
          <li>)</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'operator-list'
}
</script>

<style lang="css" scoped>
ul{
    list-style-type: none;
}
li{
    padding: 10px;
    font-size: 100px;
}
li:hover {
    background-color: #bbb;
}
</style>