<template>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
/* Customize the entire scrollbar track */
::-webkit-scrollbar {
  width: 10px; /* Width of the scrollbar */
  height: 10px; /* Height of the scrollbar for horizontal scrollbars */
}

/* Customize the scrollbar thumb */
::-webkit-scrollbar-thumb {
  background-color: #007bff; /* Set the thumb color */
  border-radius: 5px; /* Rounded corners */
}

/* Add hover effect on the scrollbar thumb */
::-webkit-scrollbar-thumb:hover {
  background-color: #0056b3; /* Darker shade for hover */
}

/* Customize the scrollbar track (background) */
::-webkit-scrollbar-track {
  background-color: #f1f1f1; /* Light gray background */
  border-radius: 5px; /* Rounded corners */
}

/* Optional: Customize the scrollbar corner (where two scrollbars meet) */
::-webkit-scrollbar-corner {
  background-color: #f1f1f1; /* Matches track background */
}
</style>
