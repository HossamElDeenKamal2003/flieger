<template>
    <div class="footer" :style="{ background: 'rgba(109, 95, 120, 1)' }">
      <div class="container">
        <!-- First Column -->
        <div class="column">
          <img :src="image" alt="Logo" class="logo" style="border-radius: 50%;" />
          <p>
            Comes with a very great service, friendly and of course comfortable at
            a very affordable price by all groups, both bottom and top.
          </p>
        </div>
  
        <!-- Second Column -->
        <div class="column" style="height: 136px;">
          <h3>Office</h3>
          <p>72 Gameat Al Dewal Al Arabeya, Ad Doqi, Dokki, Giza</p>
        </div>
  
        <!-- Third Column -->
        <div class="column">
          <h3>About Us</h3>
          <ul>
            <li>Our taxi’s</li>
            <li>Our drivers</li>
            <li>Contact us</li>
            <li>Testimonial</li>
          </ul>
        </div>
  
        <!-- Fourth Column -->
        <div class="column">
          <h3>Info</h3>
          <ul>
            <li>FAQ</li>
            <li>Cookie & help</li>
            <li>Privacy policy</li>
            <li>Terms & conditions</li>
          </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "footerComponent",
    data() {
      return {
        image: require("../assets/fego 2.png"),
      };
    },
  };
  </script>
  
  <style scoped>
  .footer {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 250px; /* Reduced height */
    padding: 20px 0; /* Adjust padding for better spacing */
    color: white;
  }
  
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 90%;
    max-width: 1200px;
    flex-wrap: wrap;
  }
  
  .column {
    flex: 1 1 20%;
    margin: 10px;
    text-align: center; /* Optional: Center text horizontally */
  }
  
  .logo {
    max-width: 100%;
    height: auto;
    margin-bottom: 10px;
  }
  
  h3 {
    margin-bottom: 10px;
    font-size: 1.2em;
  }
  
  p {
    margin: 0;
    line-height: 1.5;
  }
  
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  li {
    margin-bottom: 5px;
  }
  </style>
  