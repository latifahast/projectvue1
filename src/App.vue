<template>
  <div id="app">
    <!-- Button Click Counter Section -->
    <div class="counter-section">
      <button @click="incrementCounter" class="btn-primary">Click Me!</button>
      <p class="counter-text">Button has been clicked {{ counter }} times.</p>
    </div>
    
    <!-- Box Color Change Section -->
    <div class="color-box" :style="{ backgroundColor: boxColor }">
      Box Color
      <button @click="changeBoxColor" class="btn-secondary">Change Color</button>
    </div>
    
    <!-- Carousel Section -->
    <div id="carousel" class="carousel">
      <button @click="prevSlide" class="btn-nav">Previous</button>
      <img :src="images[currentIndex]" alt="Carousel Image" class="carousel-image">
      <button @click="nextSlide" class="btn-nav">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      counter: 0,
      boxColor: 'red',
      images: [
        './assets/image1.jpg', // Replace with actual paths to your images
        './assets/image2.jpg',
        './assets/image3.jpg'
      ],
      currentIndex: 0
    }
  },
  methods: {
    incrementCounter() {
      this.counter += 1;
    },
    changeBoxColor() {
      const colors = ['red', 'blue', 'green', 'yellow', 'purple'];
      this.boxColor = colors[Math.floor(Math.random() * colors.length)];
    },
    prevSlide() {
      this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length;
    },
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 20px;
  background-color: #f5f5f5;
}

.counter-section {
  margin-bottom: 20px;
}

.btn-primary {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}

.btn-primary:hover {
  background-color: #36a35f;
}

.counter-text {
  font-size: 18px;
  margin-top: 10px;
}

.color-box {
  width: 150px;
  height: 150px;
  margin-top: 20px;
  line-height: 150px;
  color: white;
  font-size: 16px;
  border-radius: 10px;
  display: inline-block;
  position: relative;
}

.btn-secondary {
  background-color: #ffc107;
  color: white;
  border: none;
  padding: 5px 10px;
  font-size: 14px;
  border-radius: 5px;
  cursor: pointer;
  position: absolute;
  bottom: 10px;
  right: 10px;
}

.btn-secondary:hover {
  background-color: #e0a800;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.btn-nav {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
  margin: 0 10px;
}

.btn-nav:hover {
  background-color: #0056b3;
}

.carousel-image {
  width: 300px;
  height: 200px;
  border-radius: 10px;
  object-fit: cover;
}
</style>