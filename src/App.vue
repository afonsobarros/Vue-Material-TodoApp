<template>
  <div id="app">
    <TodoContainer/>
  </div>
</template>

<script>
import TodoContainer from "./components/TodoContainer";

export default {
  name: "App",
  components: {
    TodoContainer
  }
};
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 90%;
  padding: 3% 0;
  max-width: 400px;
  margin: 0 auto;
}
</style>
