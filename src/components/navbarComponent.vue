<template>
  <div style="position: sticky; top: 0; z-index: 10000;">
    <div class="navbar">
      <div class="logo-container">
        <img :src="image" alt="Fego logo" class="logo" width="142px" height="100px">
        <img :src="fego" alt="Fego image" class="fego" width="90px" height="54px">
      </div>
      <div class="nav-list">
        <ul>
          <li><a href="#" ref="homeLink">Home</a></li>
          <li><a href="#" @click.prevent="scrollToSection('about')">About Us</a></li>
          <li><a href="#" @click.prevent="scrollToSection('fego')">Fego App</a></li>
          <li><a href="#" @click.prevent="scrollToSection('contact')">Contact Us</a></li>
        </ul>
      </div>
    </div>

    <!-- Scroll to Top Button -->
    <button class="scroll-to-top" v-if="showScrollToTop" @click="scrollToTop">
      ↑
    </button>
  </div>
</template>

<script>
export default {
  name: 'navbarComponent',
  data() {
    return {
      image: require("../assets/fego logo.png"),
      fego: require("../assets/Fego.png"),
      showScrollToTop: false, // Controls visibility of the scroll-to-top button
    };
  },
  mounted() {
    this.$refs.homeLink.focus();
    // Listen for scroll events to toggle the button visibility
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        section.scrollIntoView({ behavior: "smooth" });
      }
    },
    handleScroll() {
      this.showScrollToTop = window.scrollY > 300; // Show button after scrolling 300px
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth', // Smooth scrolling effect
      });
    },
  },
};
</script>

<style scoped>
/* Navbar styles */
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-around;
  background-color: white;
  padding: 10px 20px;

}

.logo-container {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo,
.fego {
  object-fit: contain;
}

.nav-list ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-list ul li {
  margin: 0 15px;
}

.nav-list ul li a {
  text-decoration: none;
  color: rgba(114, 114, 114, 1);
  font-size: 16px;
  font-weight: bold;
  transition: color 0.3s;
}

.nav-list ul li a:hover,
.nav-list ul li a:focus {
  color: #007bff;
  outline: none;
  border: none;
}

/* Scroll-to-top button styles */
.scroll-to-top {
  position: fixed;
  bottom: 20px;
  /* Distance from bottom */
  right: 20px;
  /* Distance from right */
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10000000;
  transition: transform 0.3s ease;
}

.scroll-to-top:hover {
  transform: scale(1.1);
  /* Slight zoom effect */
}
</style>