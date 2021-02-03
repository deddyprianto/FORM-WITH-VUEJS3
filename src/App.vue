<template>
  <Form />
</template>
<script>
import Form from "./components/Form.vue";
export default {
  name: "App",
  components: { Form },
};
</script>
<style>
body {
  background-color: #eee;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.text {
  color: #42b983;
  transition: 0.3s;
}
.change__text {
  color: red;
}
</style>
