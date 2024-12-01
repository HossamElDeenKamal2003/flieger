<template>
    <div class="contact-form">
      <h2>Contact Us</h2>
      <form @submit.prevent="submitContact" enctype="multipart/form-data">
        <div>
          <label for="username">Name:</label>
          <input type="text" id="username" v-model="form.username" required />
        </div>
        <div>
          <label for="phoneNumber">Phone Number:</label>
          <input type="text" id="phoneNumber" v-model="form.phoneNumber" required />
        </div>
        <div>
          <label for="whatsApp">WhatsApp Number:</label>
          <input type="text" id="whatsApp" v-model="form.whatsApp" />
        </div>
        <div>
          <label for="question">Your Question:</label>
          <textarea id="question" v-model="form.question" required></textarea>
        </div>
        <div>
          <label for="file">Upload File:</label>
          <input type="file" id="file" @change="handleFileUpload" />
        </div>
        <button type="submit">Submit</button>
      </form>
      <p v-if="successMessage" class="success">{{ successMessage }}</p>
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        form: {
          username: "",
          phoneNumber: "",
          whatsApp: "",
          question: "",
        },
        file: null, // For storing the uploaded file
        successMessage: "",
        errorMessage: "",
      };
    },
    methods: {
      handleFileUpload(event) {
        this.file = event.target.files[0];
      },
      async submitContact() {
        const formData = new FormData();
        formData.append("username", this.form.username);
        formData.append("phoneNumber", this.form.phoneNumber);
        formData.append("whatsApp", this.form.whatsApp);
        formData.append("question", this.form.question);
        if (this.file) {
          formData.append("file", this.file); // Attach file
        }
  
        try {
          const response = await axios.post("http://localhost:3000/contact", formData, {
            headers: { "Content-Type": "multipart/form-data" },
          });
          console.log(response)
          this.successMessage = "Your message has been sent successfully!";
          this.errorMessage = "";
          this.form = { username: "", phoneNumber: "", whatsApp: "", question: "" };
          this.file = null;
        } catch (error) {
          this.successMessage = "";
          this.errorMessage = "Failed to send message. Please try again.";
        }
      },
    },
  };
  </script>
  <style scoped>
  .contact-form {
    max-width: 80%;
    margin: auto;
    padding: 20px;
    /* border: 1px solid #ddd; */
    border-radius: 5px;
    background-color: white;
  }
  
  .contact-form div {
    margin-bottom: 15px;
  }
  
  .contact-form label {
    display: block;
    font-weight: bold;
  }
  
  .contact-form input,
  .contact-form textarea {
    width: 80%;
    padding: 10px;
    margin-top: 5px;
    /* border: 1px solid #ccc; */
    border-radius: 5px;
  }
  
  .contact-form button {
    background-color: #007bff;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .contact-form button:hover {
    background-color: #0056b3;
  }
  
  .success {
    color: green;
  }
  
  .error {
    color: red;
  }
  </style>