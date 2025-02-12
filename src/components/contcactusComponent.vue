<template>
    <div class="contact-form" id="contact">
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
        <div class="file-upload">
          <label for="file">Upload File:</label>
  
          <!-- Image preview above the button -->
          <!-- <div v-if="file" class="image-preview">
            <img :src="filePreview" alt="Image Preview" class="preview-img" />
          </div> -->
  
          <input
            type="file"
            id="file"
            @change="handleFileUpload"
            ref="fileInput"
            class="hidden-input"
          />
          
          <button
            type="button"
            class="upload-button"
            @click="$refs.fileInput.click()"
            
          >
            Select File
          </button>
          <div v-if="file" class="file-preview">
            <span>{{ file.name }}</span>
            <button type="button" class="delete-file" @click="removeFile">X</button>
          </div>
        </div>
        <button type="submit" :disabled="loading">
          Submit
          <!-- Loader while the request is being processed -->
          <span v-if="loading" class="loader"></span>
        </button>
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
      filePreview: null, // For storing the preview URL
      successMessage: "",
      errorMessage: "",
      loading: false, // To manage loading state
    };
  },
  methods: {
    handleFileUpload(event) {
      const file = event.target.files[0];
      this.file = file;
      this.filePreview = URL.createObjectURL(file); // Create a preview of the image
    },
    removeFile() {
      this.file = null;
      this.filePreview = null;
      this.$refs.fileInput.value = ""; // Reset the file input
    },
    async submitContact() {
      this.loading = true; // Show loader during the request
      const formData = new FormData();
      formData.append("username", this.form.username);
      formData.append("phoneNumber", this.form.phoneNumber);
      formData.append("whatsApp", this.form.whatsApp);
      formData.append("question", this.form.question);
      if (this.file) {
        formData.append("file", this.file); // Attach file
      }

      try {
        const response = await axios.post(
          "https://backend.fego-rides.com/admin/add-contact",
          formData,
          {
            headers: { "Content-Type": "multipart/form-data" },
          }
        );
        console.log(response);
        this.successMessage = "Your message has been sent successfully!";
        this.errorMessage = "";
        this.form = { username: "", phoneNumber: "", whatsApp: "", question: "" };
        this.file = null;
        this.filePreview = null;
      } catch (error) {
        this.successMessage = "";
        this.errorMessage = "Failed to send message. Please try again.";
      } finally {
        this.loading = false; // Hide loader when the request is finished
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
  
  /* File upload styles */
  .file-upload {
    display: flex;
    flex-direction: column;
  }
  
  .hidden-input {
    display: none;
  }
  
  .upload-button {
    background-color: #007bff;
    color: white;
    padding: 8px 12px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    width: 20%;
  }
  
  .upload-button:hover {
    background-color: #0056b3;
  }
  
  .file-preview {
    margin-top: 10px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  .file-preview span {
    font-size: 14px;
  }
  
  .delete-file {
    background-color: red;
    color: white;
    border: none;
    border-radius: 50%;
    width: 24px;
    height: 24px;
    cursor: pointer;
    font-size: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .file-upload {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center horizontally */
  justify-content: center; /* Center vertically */
  height: 150px; /* Adjust height as needed */
  padding: 20px; /* Optional: Add spacing inside the container */
}
@media screen and (max-width: 765px) {
  .upload-button {
    width: 100%; /* Makes the button take full width */
    margin-bottom: 10px; /* Optional: Add some margin between button and image */
  }

  .file-upload {
    flex-direction: column; /* Stack the button and image vertically */
    align-items: center; /* Center items horizontally */
    width: 100%; /* Ensure file upload container takes full width */
  }
}

  </style>
  