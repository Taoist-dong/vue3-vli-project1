<template>
  <div class="carousel">
    <div @click="prevSlide" class="carousel-prev-icon-left"></div>
    <div class="carousel-slides">
      <img
        v-for="(image, index) in images"
        :key="index"
        :src="image"
        v-show="index == currentSlide"
        alt="暂无图片"
      />
    </div>
    <div @click="nextSlide" class="carousel-prev-icon-right">
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
      // 每次指针加一
      this.currentSlide = (this.currentSlide + 1) % this.images.length
      console.log(this.currentSlide)
    },
    prevSlide() {
      // 每次减一，为负数时循环
      this.currentSlide = (this.currentSlide - 1 + this.images.length) % this.images.length
      console.log(this.currentSlide)
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
      // this.images[0] = this.images[nextIndex]
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
  transition: .5s transform ease-in-out;
}
.carousel-controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  justify-content: center;
}
.carousel-prev-icon-left {
  position: absolute;
  left: 10px;
  top: 55px;
  height: 50px;
  width: 40px;
  border: none;
  background-image: url(../../../assets/img/arrow-left.png);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}
.carousel-prev-icon-right {
  position: absolute;
  right: 10px;
  top: 55px;
  height: 50px;
  width: 40px;
  border: none;
  background-image: url('../../../assets/img/arrow-right.png/');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 999;
}
</style>
