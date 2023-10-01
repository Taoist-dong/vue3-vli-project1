<template>
    <div>
        <label>vant示例</label>
        <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
            <van-swipe-item>1</van-swipe-item>
            <van-swipe-item class="dif">2</van-swipe-item>
            <van-swipe-item>3</van-swipe-item>
            <van-swipe-item>4</van-swipe-item>
        </van-swipe>
        <label>自己写示例</label>
        <MySwiper></MySwiper>
    </div>
</template>
<script>
import { createApp } from 'vue';
import { Swipe, SwipeItem } from 'vant';
import MySwiper from "./components/SwiperItem.vue"

const app = createApp();
app.use(Swipe);
app.use(SwipeItem);
// app.components('MySwiper', MySwiper);
console.log("in"+Swipe);
export default {
  components: {
    MySwiper
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