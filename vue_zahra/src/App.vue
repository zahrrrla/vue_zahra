<template>
  <div id="app">
    <!-- Button Counter -->
    <button @click="incrementCounter">Klik Saya!</button>
    <p>Counter: {{ counter }}</p>

    <!-- Box dengan warna -->
    <div :style="{ backgroundColor: boxColor, width: '100px', height: '100px', marginTop: '20px' }"></div>
    <button @click="changeBoxColor">Ubah Warna Box</button>

    <!-- Button untuk mengubah background body -->
    <button @click="changeBodyBackground">Ubah Background Body</button>

    <!-- Image Carousel -->
    <div class="carousel">
      <button @click="prevImage">Back</button>
      <img :src="images[currentImage]" alt="Image Carousel" class="carousel-image">
      <button @click="nextImage">Lanjut</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
      boxColor: 'lightblue',
      images: [
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQjhxTHYWPaOnEK9_1DQwQOxgvBVNIJw6LI0w&s', // Gambar Pemandangan 1
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRFyGJ9df20G3AdPV12z5AGytoQbkvEp5R_Bw&s', // Gambar Pemandangan 2
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS2ws-ItsCmNAAYiutuHqZkPx2ys4YrHQiWLA&s'  // Gambar Pemandangan 3
      ],
      currentImage: 0
    };
  },
  methods: {
    incrementCounter() {
      this.counter += 1;
    },
    changeBoxColor() {
      const randomColor = '#' + Math.floor(Math.random() * 16777215).toString(16);
      this.boxColor = randomColor;
    },
    changeBodyBackground() {
      const randomColor = '#' + Math.floor(Math.random() * 16777215).toString(16);
      document.body.style.backgroundColor = randomColor;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    }
  }
};
</script>

<style scoped>
button {
  font-size: 16px;
  padding: 10px;
  margin: 10px;
}
p {
  font-size: 20px;
}
.carousel {
  display: flex;
  align-items: center;
  margin-top: 20px;
}
.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
  margin: 0 10px;
}
</style>
