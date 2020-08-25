<template>
  <div id="app">
    <div>
        <!-- Provides extra visual weight and identifies the primary action in a set of buttons -->
        <mdb-btn color="primary">Primary</mdb-btn>

        <!-- Default button -->
        <mdb-btn color="default">Default</mdb-btn>

        <!-- Secondary button -->
        <mdb-btn color="secondary">Secondary</mdb-btn>

        <!-- Indicates a successful or positive action -->
        <mdb-btn color="success">Success</mdb-btn>

        <!-- Contextual button for informational alert messages -->
        <mdb-btn color="info">Info</mdb-btn>

        <!-- Indicates caution should be taken with this action -->
        <mdb-btn color="warning">Warning</mdb-btn>

        <!-- Indicates a dangerous or potentially negative action -->
        <mdb-btn color="danger">Danger</mdb-btn>
    </div>
  </div>
</template>

<script>
import { mdbContainer, mdbRow, mdbCol, mdbBtn } from "mdbvue";
export default {
  name: 'App',
  components: {
    mdbContainer,
    mdbRow,
    mdbCol,
    mdbBtn
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap');

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
