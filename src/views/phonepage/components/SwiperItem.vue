<template>
  <div class="carousel">
    <div class="carousel-slides">
      <img v-for="(image, index) in images" :key="index" :src="image" v-show="index == currentSlide" alt="Slide" />
    </div>
    <div class="carousel-controls">
      <button @click="prevSlide" :disabled="currentSlide === 0">
        <span class="carousel-prev-icon" v-if="currentSlide !== 0">&lt;</span>
        <span class="carousel-prev-icon" v-else>&lt;</span>
      </button>
      <button @click="nextSlide" :disabled="currentSlide === images.length - 1">
        <span class="carousel-next-icon" v-if="currentSlide !== images.length - 1">&gt;</span>
        <span class="carousel-next-icon" v-else>&gt;</span>
      </button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      images: [
        '/src/assets/img/sakuraTree01.jpeg',
        '/src//assets/img/starrySky.jpg',
        '/src//assets/img/starrySky02.jpg'
        // ... 更多图片
      ],
      currentSlide: 0
    }
  },
  created() {},
  mounted() {
    this.startSlideshow()
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.images.length
      console.log(this.currentSlide);
    },
    prevSlide() {
      this.currentSlide = (this.currentSlide - 1 + this.images.length) % this.images.length

    },
    startSlideshow() {
      this.interval = setInterval(() => {
        this.navigateToNext(this.currentSlide)
      }, 3000)
    },
    stopSlideshow() {
      clearInterval(this.interval)
    },
    navigateToNext() {
      const currentIndex = this.images.indexOf(this.images[this.currentSlide])
      const nextIndex = (currentIndex + 1) % this.images.length
      this.images[0] = this.images[nextIndex]
    }
  }
}
</script>
<style scoped>
.carousel {
  position: relative;
  width: 100%;
  overflow: hidden;
}
.carousel-slides {
  display: flex;
  width: 100%;
  height: 100%;
}
.carousel-slides img {
  width: 100%;
  height: 100%;
}
.carousel-controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  justify-content: center;
}
.carousel-controls button {
  margin: 0 10px;
  background: none;
  border: none;
  text-decoration: underline;
  cursor: pointer;
}
</style>
