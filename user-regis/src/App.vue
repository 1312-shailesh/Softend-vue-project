<template>
  <router-view />
</template>

<script>

export default {
  name: 'App',


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.logo {
  width: 100px;

}

.register input,
.login input {
  width: 300px;
  height: 10px;
  padding: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid #2980b9;
  border-radius: 30px;

}

.register button,
.login button {
  width: 225px;
  height: 40px;
  border: 1px solid #2980b9;
  border-radius: 30px;
  background-color: #2980b9;
}

.register button:hover,
.login button:hover {
  background-color: aqua;
}
.regsitered {
  margin-left: auto;
  margin-right: auto;
  align-items: center;


}
</style>
