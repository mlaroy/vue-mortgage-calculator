<template>
  <div id="app">
    <div class="container">
      <h1>Mortgage Calculator</h1>
      <p>Built with Vue.</p>
      <Form />
      <div class="disclaimer">
        Disclaimer: This is a very simplistic tool to estimate mortgages. I created the logic based on <a href="https://en.wikipedia.org/wiki/Mortgage_calculator">this wikipedia article</a>,
        and this should in no way be considered an authoritative reference, accurate as it may be. Talk to your bank or mortgage provider.
      </div>
      <hr>
      <p>
        By <a href="https://mikelaroy.ca/">Michael LaRoy</a> |
        <a href="https://github.com/mlaroy/vue-mortgage-calculator">Github Repo</a>
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

.disclaimer {
  margin-top: 200px;
  font-size: 12px;
}

.container {
  margin: 0 auto;
  max-width: 960px;
  padding: 1rem;
}
</style>
