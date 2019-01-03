<template>
  <div id="app">
    <Bag :phones="phones"/>
    <Grid :phones="phones"/>
  </div>
</template>

<script>
import Bag from './components/Bag';
import Grid from './components/Grid';
import axios from 'axios';

export default {
  name: 'App',

  components: {
    Bag,
    Grid
  },

  data() {
    return {
      phones: []
    };
  },

  mounted() {
    axios('https://apeps.kiev.ua/post/getphones')
      .then(response => {
        for(let i = 0; i < response.data.length; i++){
          response.data[i].purchasedCount = 0;
        }
        this.phones = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
