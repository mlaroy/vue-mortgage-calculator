<template>
  <div id="app">
    <div class="container">
      <h1>Mortgage Calculator</h1>
      <p>Built with Vue.</p>
      <Form />
      <hr>
      <p>
        By <a href="https://mikelaroy.ca/">Michael LaRoy</a> |
        <a href="">Github Repo</a>
      </p>
    </div>
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  background: #eee;
  min-height: 100vh;
}

body {
  margin: 0;
  padding: 0;
}

.container {
  margin: 0 auto;
  max-width: 960px;
  padding: 1rem;
}
</style>
