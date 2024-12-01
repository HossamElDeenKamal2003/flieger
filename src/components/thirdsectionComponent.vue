<template>
    <div class="parent" id="fego">
        <div class="left-side">
            <div>
                <img :src="image" alt="">
            </div>
        </div>
        <div class="right-side">
            <div>
                <h1>connected with all circles and wherever and whenever</h1>
            </div>
            <div>
                <p>FEGO reaches all people so that they can use the facilities that we provide, very special comfort and security</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "thirdSection",
    data(){
        return{
            image: require("../assets/mobile-screen-frame-travel-collage-design_23-2151708200 1 (1).png")
        }
    }
}
</script>

<style scoped>
/* Parent container */
.parent {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 20px;
  padding: 40px;
  background-color: white;
  flex-wrap: wrap; /* Makes it responsive */
}

/* Left-side container */
.left-side {
  flex: 1;
  max-width: 35%; /* Adjust the size proportionally */
  display: flex;
  justify-content: center;
  align-items: center;
}

.left-side img {
  width: 100%; /* Makes the image responsive */
  max-width: 818px; /* Limits the image size */
  border-radius: 10px; /* Adds smooth corners to the image */
  object-fit: cover; /* Ensures the image retains its aspect ratio */
}

/* Right-side container */
.right-side {
  flex: 1;
  max-width: 30%;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.right-side h1 {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  line-height: 1.4;
  text-align: center; /* Centers the text */
}

.right-side p {
  font-size: 1rem;
  color: #555;
  line-height: 1.6;
  text-align: center; /* Centers the text */
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .parent {
    flex-direction: column;
    align-items: center;
  }

  .left-side,
  .right-side {
    max-width: 100%; /* Full width for smaller screens */
    text-align: center;
  }

  .left-side img {
    max-width: 300px; /* Scales the image appropriately for smaller screens */
  }

  .right-side h1,
  .right-side p {
    text-align: center;
  }
}
</style>
