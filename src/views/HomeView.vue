<template>
  <div class="parent">
    <div class="border"></div>
    <nav class="navbar navbar-expand-lg  bg-light">
      <div class="container-fluid" style="background-color: #af9adb;">
        <div class="logo">
          <img src="../assets/shared image.jpeg" alt="Flieger Logo" class="navbar-brand">
        </div>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#">Home <span class="visually-hidden">(current)</span></a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">About Us</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Flieger App</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Contact Us</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="homeSection">
      <div class="first">
        <div class="image">
          <img src="../assets/shared image.jpeg" alt="Flieger Logo">
        </div>
        <div class="text">
          <h2>Flieger</h2>
          <div>
            <h3>On Site</h3>
            <h3>On Time</h3>
            <h3>On Budget</h3>
          </div>
        </div>
      </div>
      <div class="footer-text">
        <h2>Download The Application And Book Your Trip Now : </h2><br>
        <a href="#">here is link</a>
      </div>
    </div>
    
    <h1>About Us</h1>
    <div class="about">
      <div>
        <p>Attention, everyone! Flieger Technology proudly presents the best riding book system, designed to elevate your riding experience. Our innovative system combines advanced features with user-friendly design, ensuring seamless organization and efficiency for all your riding needs. Join us in revolutionizing the way you ride!</p>
        <p>  
          On Site
          On Time
          On Budge
      </p>
    </div>
  </div>
    <h1>Contact Us</h1>
    <div class="contact-form-section">
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="username">Username:</label>
          <input 
            type="text" 
            id="username" 
            v-model="form.username" 
            placeholder="Enter your username"
            :class="{'is-invalid': errors.username}"
          />
          <div v-if="errors.username" class="error">{{ errors.username }}</div>
        </div>

        <div class="form-group">
          <label for="phone">Phone Number:</label>
          <input 
            type="tel" 
            id="phone" 
            v-model="form.phoneNumber" 
            placeholder="Enter your phone number"
            :class="{'is-invalid': errors.phoneNumber}"
          />
          <div v-if="errors.phoneNumber" class="error">{{ errors.phoneNumber }}</div>
        </div>

        <div class="form-group">
          <label for="whatsapp">WhatsApp:</label>
          <input 
            type="tel" 
            id="whatsapp" 
            v-model="form.whatsApp" 
            placeholder="Enter your WhatsApp number"
            :class="{'is-invalid': errors.whatsApp}"
          />
          <div v-if="errors.whatsApp" class="error">{{ errors.whatsApp }}</div>
        </div>

        <div class="form-group">
          <label for="questions">Questions:</label>
          <textarea 
            id="questions" 
            v-model="form.question" 
            placeholder="Enter your questions"
            :class="{'is-invalid': errors.question}"
          ></textarea>
          <div v-if="errors.question" class="error">{{ errors.question }}</div>
        </div>
        <div class="sub" style="display: flow;">
          <button class="submit-button btn btn-primary" >Submit</button>
        </div>
      </form>
    </div>
  
  </div>
</template>


<script>
import axios from 'axios';
export default {
  name: 'HomeView',
  data() {
    return {
      form: {
        username: '',
        phoneNumber: '',
        whatsApp: '',
        question: '',
      },
      errors: {
        username: null,
        phoneNumber: null,
        whatsApp: null,
        question: null,
      }
    };
  },
  methods: {
    validateForm() {
      let isValid = true;
    
      // Validate username
      if (!this.form.username) {
        this.errors.username = 'Username is required';
        isValid = false;
      } else {
        this.errors.username = null;
      }
    
      // Validate phone
      if (!this.form.phoneNumber) {
        this.errors.phoneNumber = 'Phone number is required';
        isValid = false;
      } else if (!/^\d+$/.test(this.form.phoneNumber)) {
        this.errors.phoneNumber = 'Phone number must be numeric';
        isValid = false;
      } else {
        this.errors.phoneNumber = null;
      }
    
      // Validate WhatsApp
      if (!this.form.whatsApp) {
        this.errors.whatsApp = 'WhatsApp number is required';
        isValid = false;
      } else if (!/^\d+$/.test(this.form.whatsApp)) {
        this.errors.whatsApp = 'WhatsApp number must be numeric';
        isValid = false;
      } else {
        this.errors.whatsApp = null;
      }
    
      // Validate questions
      if (!this.form.question) {
        this.errors.question = 'Questions field cannot be empty';
        isValid = false;
      } else {
        this.errors.question = null;
      }
    
      return isValid;
    },
    
    submitForm() {
      if (this.validateForm()) {
        axios.post('https://fliegertechnology.onrender.com/admin/add-contact', this.form)
          .then(response => {
            console.log(response.data);
            alert('Your Questions Sent Successfully, We Will Contact You');
          })
          .catch(error => {
            console.log(error); // Fix typo
          });
      }
    }    
  }
};
</script>

<style scoped>
.logo img {
  max-width: 100px; /* Adjust size as needed */
  height: auto;
  border-radius: 50%;
}
.navbar{
  background-color: #af9adb;
}

.navbar-toggler:focus {
  outline: none; /* Remove the focus outline */
  box-shadow: none; /* Remove any box shadow */
}

.navbar-toggler {
  border: none;
}

.border {
  height: 40px;
  background-color: #7259aa;
}

a {
  font-weight: bold;
  padding: 15px;
  font-size: larger;
  color: #7259aa;
  transition: transform 0.3s ease; 
}

a:hover {
  transform: translateY(-12px);
}

.homeSection {
  background-color: #af9adb;
  height: 83vh;
  /*display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;*/
}

.homeSection .first{
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
}

.homeSection .first .image img {
  border-radius: 50%;
  width: 500px;
  opacity: 0; /* Start hidden */
  animation: slideIn 1s forwards; /* Apply the animation */
  border-bottom: 15px solid #7259aa;
}

@keyframes slideIn {
  0% {
    transform: translateX(-100%); /* Start from the left */
    opacity: 0; /* Start hidden */
  }
  100% {
    transform: translateX(0); /* Move to the original position */
    opacity: 1; /* Fade in */
  }
}

.homeSection .text h2 {
  color: whitesmoke;
  font-weight: bold;
  font-size: 5em;
  animation: slideUp 1s forwards;
}


@keyframes slideUp {
  0% {
    transform: translateY(100%); /* Start from the left */
    opacity: 0; /* Start hidden */
  }
  100% {
    transform: translateY(0); /* Move to the original position */
    opacity: 1; /* Fade in */
  }
}


.homeSection .first .text div h3 {
  font-weight: bold;
  color: whitesmoke;
  font-size: 3em;
  transition: transform 0.3s ease; 
  animation: slideIn 2s forwards;
}

@keyframes slideIn {
  0% {
    transform: translateX(100%); /* Start from the left */
    opacity: 0; /* Start hidden */
  }
  100% {
    transform: translateX(0); /* Move to the original position */
    opacity: 1; /* Fade in */
  }
}

.homeSection .first .text div h3:hover {
  color: #7259aa;
  transform: translateY(-12px);
}

h1 {
  color: #7259aa;
  font-weight: bold;
  margin-top: 10px;
  font-size: 4em;
  position: relative; /* Required for positioning the pseudo-element */
  overflow: hidden; /* Ensures the line stays within the h1 */
}

h1::after {
  content: '';
  position: absolute;
  left: 100%; /* Start off the right side */
  bottom: 0; /* Align the line to the bottom */
  width: 100%; /* Width of the line */
  height: 2px; /* Thickness of the line */
  background-color: #7259aa; /* Color of the line */
  transition: left 1s ease; /* Smooth transition for the line */
}

h1:hover::after {
  left: 0; /* Move the line to the left on hover */
}


@media (max-width: 1439px) {
  .homeSection .image img {
    width: 300px;
  }
}

.about{
  height: 100vh;
  background-color: #af9adb;
  margin-top: 15px;
}
.homeSection {
  background-color: #af9adb;
  height: 83vh;
  display: flex;
  flex-direction: column; /* Stack children vertically */
  justify-content: space-between; /* Space between the image/text and footer text */
}

.homeSection .first {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex: 1; /* Take remaining space */
}

.footer-text {
  text-align: center; /* Center align the footer text */
  margin-bottom: 20px; /* Add some margin at the bottom */
  color: whitesmoke;
}

.about{
  display: flex;
  align-items: center;
  justify-content: center;
}

.about p{
  color: white;
  font-weight: bold;
  font-size: 3em;
}

@media (max-width: 1439px) {
  .border {
    height: 25px;
  }
  .homeSection .first .image img {
    width: 300px;
  }
  .homeSection {
    height: 131vh;
  }
}
@media (max-width: 1439px){
  .about p{
    color: white;
    font-weight: bold;
    font-size: 1em;
  }
}
.contact-form-container {
  background-color: #f9f9f9;
  padding: 50px 20px;
  margin: 30px auto;
  border-radius: 10px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  width: 80%;
  max-width: 700px;
}

.contact-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  font-weight: bold;
  color: #333;
}

.form-control {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 16px;
}

.form-control:focus {
  border-color: #7259aa;
  box-shadow: 0 0 5px rgba(114, 89, 170, 0.5);
}

.submit-btn {
  background-color: #7259aa;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  font-size: 18px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.submit-btn:hover {
  background-color: #af9adb;
}

.contact-form-section{
  display: flex;
  justify-content: center;
}

.contact-form-section div{
    display: grid;
    grid-template-columns: 1fr 1fr;
}

.contact-form-section div input{
  width: 250px;
  padding: 5px;
}
.contact-form-section div textarea{
  width: 250px;
  padding: 5px;
}
/* Media Queries */
@media (max-width: 768px) {
  .contact-form-container {
    width: 90%;
    padding: 20px 10px;
  }
}

.submit-button{
  width: fit-content;
}

.sub{
  display: flow;
}
</style>


