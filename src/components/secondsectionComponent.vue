<template>
    <div class="parent">
      <!-- Left Side Content -->
      <div class="left-side">
        <div>
          <h1>We will make you very special with our service</h1>
        </div>
        <div>
          <p>There are many benefits that you will get at FEGO, and for sure you will be comfortable and safe with us with great facilities and benefits.</p>
        </div>
      </div>
  
      <!-- Right Side Cards -->
      <div class="right-side">
        <!-- Card: On Site -->
        <div class="card">
          <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M40.6202 40.6H9.2002C7.0002 40.6 5.2002 38.8 5.2002 36.6V14.62C5.2002 12.42 7.0002 10.62 9.2002 10.62H40.6202C42.8202 10.62 44.6202 12.42 44.6202 14.62V36.6C44.6202 38.8 42.8402 40.6 40.6202 40.6Z" fill="#9C7AE6" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path d="M5.2002 18.2H44.6202" stroke="#DCD9EB" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path d="M15.4805 13.78V7.19995" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path d="M34.3403 13.78V7.19995" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
          <h1>On Site</h1>
          <p>The drivers will come to your location or another designated location of your choice.</p>
        </div>
  
        <!-- Card: On Time -->
        <div class="card">
          <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M21.7644 9.40552C11.9401 9.40552 4 17.3681 4 27.1699C4 36.9942 11.9626 44.9343 21.7644 44.9343C31.5886 44.9343 39.5288 36.9717 39.5288 27.1699H21.7644V9.40552Z" fill="#9C7AE6" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
            <path d="M27.0356 4C36.8599 4 44.8 11.9626 44.8 21.7644H27.0356V4Z" fill="#9C7AE6" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
          <h1>On Time</h1>
          <p>The driver arrives at the pickup location at the promised time, ensuring timely trips for passengers.</p>
        </div>
  
        <!-- Card: On Budge -->
        <div class="card">
          <svg width="35" height="39" viewBox="0 0 35 39" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M23.1351 34.235L17.5668 37.3116L11.9985 34.2133C5.8018 30.79 1.9668 24.2683 1.9668 17.1833V1.79999H33.1451V17.1833C33.1451 24.2683 29.3101 30.79 23.1351 34.235Z" fill="#9C7AE6" stroke="#9C7AE6" stroke-width="2.4" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
          <h1>On Budget</h1>
          <p>Before booking, users can view the estimated fare, avoiding unexpected charges.</p>
        </div>
      </div>
    </div>
  </template>
  
<script>
export default {
    name: "secondSection"
}
</script>
<style scoped>
/* Parent container */
.parent {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 40px;
  gap: 20px;
  flex-wrap: wrap;
  background-color: white;
}

/* Left-side content */
.left-side {
  flex: 1;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.left-side h1 {
  font-size: 4rem;
  font-weight: bold;
  color: #333;
  line-height: 1.4;
  margin-bottom: 20px;
}

.left-side p {
  font-size: 1.5rem;
  color: #555;
  line-height: 1.6;
}

/* Right-side cards */
.right-side {
  display: flex;
  flex-direction: column;
  gap: 20px;
  flex: 1;
  max-width: 600px;
}

/* Individual card */
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  transition: transform 0.2s;
  height: 300px;
  border: none;
}

/* SVG icons */
.card svg {
  margin-bottom: 15px;
}

/* Card title */
.card h1 {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  margin: 10px 0;
}

/* Card description */
.card p {
  font-size: 1.5rem;
  color: #666;
  line-height: 1.5;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .parent {
    flex-direction: column;
    align-items: center;
  }
  .left-side h1{
    font-size: 2rem;
  }
  .left-side p{
    font-size: 1rem;
  }
  .left-side,
  .right-side {
    max-width: 100%;
  }
}
</style>

