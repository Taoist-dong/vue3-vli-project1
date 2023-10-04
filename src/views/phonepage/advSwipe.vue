<template>
    <div>
        <label>vant示例</label>
        <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white" @change="onChange">
            <van-swipe-item>vant-swipe</van-swipe-item>
            <van-swipe-item class="dif">2</van-swipe-item>
            <van-swipe-item>3</van-swipe-item>
            <van-swipe-item>4</van-swipe-item>
        </van-swipe>

        <label>自己写示例</label>
        <MySwiper></MySwiper>
        <label>动画</label>
        <SwiperAni></SwiperAni>
        <label>图片动画</label>
        <ImageAni></ImageAni>
    </div>
</template>
<script>
import MySwiper from "./components/SwiperItem.vue";
import SwiperAni from "./components/swipeAni.vue"
import ImageAni from "./components/ImageAni.vue"

export default {
  components: {
    MySwiper,
    SwiperAni,
    ImageAni
  },
  methods: {
      onChange() {
        //change action
      }
  }
}
</script>
<style>
.my-swipe .van-swipe-item {
    color: #fff;
    font-size: 20px;
    line-height: 150px;
    text-align: center;
    background-color: #39a9ed;
  }
.my-swipe .dif {
  background-color: #ccdba3;
}
</style>