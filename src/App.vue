<template>
  <div id="app">
    <UserCard />
  </div>
</template>
<script>
import UserCard from "./components/UserCard";

export default {
  name: "App", //El nombre del componente que estamos creando
  components: {
    UserCard,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
.shadow {
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  background-color: rgb(243, 243, 243);
  height: 100vh;
  width: 100%;
}
.container {
  max-width: 900px;
  margin: 0 auto;
  position: relative;
}
</style>
