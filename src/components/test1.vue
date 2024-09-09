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
    background-color: white; /* สีพื้นหลังของปุ่ม */
    color: black; /* สีตัวอักษรของปุ่ม */
    border: 2px solid black; /* ขอบของปุ่ม */
    padding: 10px 20px; /* ระยะห่างด้านในของปุ่ม */
    font-size: 16px; /* ขนาดตัวอักษร */
    cursor: pointer; /* เปลี่ยนเคอร์เซอร์เมื่อวางบนปุ่ม */
    border-radius: 5px; /* มุมปุ่มกลม */
    transition: background-color 0.3s, border-color 0.3s; /* การเปลี่ยนสีพื้นหลังและสีขอบเมื่อโฮเวอร์ */
    margin: 5px; /* ระยะห่างรอบปุ่ม */
  }
  
  button:hover {
    background-color: #f0f0f0; /* สีพื้นหลังเมื่อวางเมาส์เหนือปุ่ม */
    border-color: #333; /* สีขอบเมื่อวางเมาส์เหนือปุ่ม */
  }
  </style>
  