<template>
  <div id='App'>
  <h1>{{ firstName }}</h1>
  <h2>{{ num > 1 ? 'Number: > 1' : 'Numberone' }}</h2>
  <h3>{{ obj.age }}</h3>
  </div>

</template>

<script>

export default {
  name: 'App',

  data: () => ({
    firstName: 'roman',
    num: 7,
    obj: {
      age: 30,
    },
  }),
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
