<template>
    <div class="parent">
      <div class="left-side">
        <div>
          <h1>be the first with fego</h1>
        </div>
        <div>
          <p>
            Comes with a very great service, friendly and of course comfortable at
            a very affordable price by all groups, both bottom and top
          </p>
        </div>
        <div class="trip-image">
          <img :src="tripImage" alt="trips image" />
        </div>
        <div id="icons">
          <div class="google">
            <div class="icon-container">
              <h2>User App</h2>
              <a href="https://play.google.com/store/apps/details?id=com.fego.user">
                <img :src="googleIconUser" alt="Google Play Store" class="icon" />
              </a>
            </div>
            <div class="icon-container">
              <h2>Driver App</h2>
              <a href="https://play.google.com/store/apps/details?id=com.fego.driver">
                <img :src="googleIconDriver" alt="Google Play Store" class="icon" />
              </a>
            </div>
          </div>
          <div class="apple">
            <div class="icon-container">
              <h2>User App</h2>
              <a href="https://apps.apple.com/eg/app/fego/id6740404406">
                <img :src="appleIconUser" alt="Apple App Store" class="icon" />
              </a>
            </div>
            <div class="icon-container">
              <h2>Driver App</h2>
              <a href="https://apps.apple.com/eg/app/fego-driver/id6740406370">
                <img :src="appleIconDriver" alt="Apple App Store" class="icon" />
              </a>
            </div>
          </div>
        </div>
      </div>
      <div class="right-side">
        <img :src="rightsideImage" alt="" width="100%" />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "firtsSection",
    data() {
      return {
        tripImage: require("../assets/trips.png"),
        rightsideImage: require("../assets/rightSide image.png"),
        googleIconUser: require("../assets/googleIcon.png"),
        googleIconDriver: require("../assets/googleIcon.png"),
        appleIconUser: require("../assets/appleIcon.png"),
        appleIconDriver: require("../assets/appleIcon.png"),
      };
    },
  };
  </script>
  
  <style scoped>
  /* Parent container styles */
  .parent {
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;
    padding: 40px;
    background-color: white;
  }
  
  /* Left side container styles */
  .left-side {
    max-width: 600px;
    padding: 20px;
    text-align: left;
  }
  
  /* Heading styles */
  .left-side h1 {
    font-size: 36px;
    font-weight: bold;
    margin-bottom: 20px;
    text-transform: capitalize;
    color: #333;
  }
  
  /* Paragraph styles */
  .left-side p {
    font-size: 16px;
    line-height: 1.6;
    color: #555;
    margin-bottom: 30px;
  }
  
  /* Trip image container styles */
  .trip-image img {
    width: 100%;
    max-width: 400px;
    border-radius: 10px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    object-fit: cover;
  }
  
  /* Icons container styles */
  #icons {
    margin-top: 20px;
  }
  
  .google,
  .apple {
    display: flex;
    justify-content: space-around;
    gap: 20px; /* Adds space between the icon containers */
    margin-bottom: 20px; /* Adds space between Google and Apple sections */
  }
  
  .icon-container {
    text-align: center;
  }
  
  .icon-container h2 {
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 10px;
    color: #333;
  }
  
  .icon-container a {
    display: inline-block;
    transition: transform 0.3s ease;
  }
  
  .icon-container a:hover {
    transform: scale(1.1); /* Adds a hover effect to the icons */
  }
  
  .icon {
    width: 150px; /* Adjust the size of the icons */
    height: auto;
    border-radius: 10px; /* Adds rounded corners to the icons */
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); /* Adds a subtle shadow */
  }
  </style>
