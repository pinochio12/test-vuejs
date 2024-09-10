<template>
    <div>
      <label for="inputNumber">Input : </label>
      <input v-model="inputNumber" id="inputNumber" type="number" />
      <button @click="generatePattern">Submit</button>
      <div v-if="pattern.length">
        <div v-for="(line, index) in pattern" :key="index">{{ line }}</div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        inputNumber: 0,
        pattern: [],
      };
    },
    methods: {
      generatePattern() {
        this.pattern = [];
        let number = parseInt(this.inputNumber);
  
        // Add ascending stars
        for (let i = 1; i <= number; i++) {
          this.pattern.push('*'.repeat(i));
        }
  
        // Add descending stars
        for (let i = number - 1; i >= 1; i--) {
          this.pattern.push('*'.repeat(i));
        }
      },
    },
  };
  </script>
  
  <style scoped>
  div {
    margin-top: 10px;
  }
  
  button {
    background-color: white;
    color: black;
    border: 2px solid black;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s, border-color 0.3s;
    margin: 5px;
  }
  
  button:hover {
    background-color: #f0f0f0;
    border-color: #333;
  }
  </style>
  
