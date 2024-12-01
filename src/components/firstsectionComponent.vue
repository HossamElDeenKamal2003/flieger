<template>
    <div class="parent">
        <div class="left-side">
            <div>
                <h1>be the first with fego</h1>
            </div>
            <div>
                <p>Comes with a very great service, friendly and of course comfortable at a very affordable price by all groups, both bottom and top</p>
            </div>
            <div class="trip-image">
                <img :src="tripImage" alt="trips image">
            </div>
        </div>
        <div class="right-side">
            <img :src="rightsideImage" alt="" width="100%">
        </div>

    </div>
</template>

<script>
    export default{
        name: 'firtsSection',
        data(){
            return{
                tripImage: require("../assets/trips.png"),
                rightsideImage: require("../assets/rightSide image.png")
            }
        }
    }
</script>

<style scoped>
/* Parent container styles */
.parent {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
  padding: 40px;
  background-color: white; /* Light background color */
}

/* Left side container styles */
.left-side {
  max-width: 600px; /* Restricts the width for better readability */
  padding: 20px;
  text-align: left;
}

/* Heading styles */
.left-side h1 {
  font-size: 36px;
  font-weight: bold;
  margin-bottom: 20px;
  text-transform: capitalize;
  color: #333; /* Darker text for better contrast */
}

/* Paragraph styles */
.left-side p {
  font-size: 16px;
  line-height: 1.6;
  color: #555; /* Slightly lighter than heading */
  margin-bottom: 30px;
}

/* Trip image container styles */
.trip-image img {
  width: 100%;
  max-width: 400px;
  border-radius: 10px; /* Adds a slight curve to the corners */
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); /* Adds a subtle shadow */
  object-fit: cover; /* Ensures the image fits the container */
}
</style>
