<template>
  <div class="carousel">
    <div @click="prevSlide" class="carousel-prev-icon-left"></div>
    <div class="carousel-slides">
      <img
        v-for="(image, index) in images"
        :key="index"
        :src="image"
        :style="{left: index * 100 + '%', 'transform': dynamicstyle}"
        alt="暂无图片"
      />
    </div>
    <div @click="nextSlide" class="carousel-prev-icon-right"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      images: [
        '/src/assets/img/sakuraTree01.jpeg',
        '/src/assets/img/starrySky.jpg',
        '/src/assets/img/starrySky02.jpg'
        // ... 更多图片
      ],
      dynamicstyle: "", //动态样式
      currentSlide: 0, //播放序号
      interval: Object,
    }
  },
  mounted() {
    // 自动播放动画
    this.startSlideshow()
  },
  methods: {
    nextSlide() {
      // 每次指针加一
      this.currentSlide = (this.currentSlide + 1) % this.images.length
      this.setStyle();
    },
    prevSlide() {
      // 每次减一，为负数时循环
      this.currentSlide = (this.currentSlide - 1 + this.images.length) % this.images.length;
      this.setStyle();
    },
    // 图片动画
    setStyle() {
      this.dynamicstyle = `translatex(-${this.currentSlide*100}%)`
    },
    // 定时器
    startSlideshow() {
      this.interval = setInterval(() => {
        this.currentSlide = (this.currentSlide + 1) % this.images.length;
        this.setStyle();
      }, 3000)
    },
    stopSlideshow() {
      clearInterval(this.interval)
    }
  }
}
</script>
<style scoped>
.carousel {
  position: relative;
}
.carousel-slides {
  position: relative;
  width: 320px;
  height: 173px;
  overflow: hidden;
}
.carousel-slides img {
  display: inline-block;
  position: absolute;
  width: inherit;
  margin: 0;
  padding: 0;
  top: 0;
  left: 0;
  height: 100%;
  transition: 0.5s transform ease-in-out;
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
  background-image: url(../../../assets/img/arrow-l.png);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 999;
}
.carousel-prev-icon-right {
  position: absolute;
  right: 10px;
  top: 55px;
  height: 50px;
  width: 40px;
  border: none;
  background-image: url('../../../assets/img/arrow-r.png/');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 999;
}
</style>
