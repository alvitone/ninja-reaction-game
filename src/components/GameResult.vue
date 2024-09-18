<template>
    <h2 v-if="showResult">Reaction Time: {{ output }} ms - {{ finalResult }}</h2>
  </template>
  
  <script>
  export default {
    name: 'GameResult',
    props: {
      showResult: {
        type: Boolean,
        default: false,
      },
      output: {
        type: Number,
        required: true,
      },
    },
    computed: {
      finalResult() {
        return this.output < 250 ? "Fast" : "Slow";
      },
    },
  };
  </script>
  
  <style>
  /* Add any styles you want here */
  </style>
  