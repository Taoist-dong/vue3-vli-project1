<template>
<div>
  <ul class="slider">
    <input type="radio" id="control-1" name="control" checked/>
    <input type="radio" id="control-2" name="control"/>
    <input type="radio" id="control-3" name="control"/>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <div class="control-nav">
      <label for="control-1"></label>
      <label for="control-2"></label>
      <label for="control-3"></label>
    </div>
  </ul>
</div>
</template>
<style scoped>
.slider{
  position: relative;
  width: 320px; /* 调整为适合你的轮播图的宽度 */
  height: 170px;
  overflow: hidden;
  list-style: none;
  background: #eee;
  margin: 0;
  padding: 0;
}

.slider li {
  position: absolute;
  font-size: 20px;
  width: inherit;
  height: inherit;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 0;
  top: 0;
  left: 0;
  transition: .5s transform ease-in-out;
}

li:nth-of-type(1){
  background: rgb(224, 170, 170);
}
li:nth-of-type(2) {
  background-color: rgb(199, 212, 141);
  left: 100%
}
li:nth-of-type(3) {
  background-color: rgb(142, 201, 209);
  left: 200%
}
.control-nav {
  position: absolute;
  width: 100%;
  bottom: 20px;
  text-align: center;
}
.control-nav label{
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #fff;
  border-radius: 50%;
  margin: 0 3px;
  border: 2px solid #fff;
}
.slider input {
  display: none;
}
.slider input[type="radio"]:nth-child(1):checked ~ .control-nav label:nth-child(1) {
  background: rgb(86, 165, 218);
}
.slider input[type="radio"]:nth-child(2):checked ~ .control-nav label:nth-child(2) {
  background: rgb(86, 165, 218);
}
.slider input[type="radio"]:nth-child(3):checked ~ .control-nav label:nth-child(3) {
  background: rgb(86, 165, 218);
}
.slider input[type="radio"]:nth-child(1):checked ~ li {
  transform: translatex(0%);
}
.slider input[type="radio"]:nth-child(2):checked ~ li {
  transform: translatex(-100%);
}
.slider input[type="radio"]:nth-child(3):checked ~ li {
  transform: translatex(-200%);
}
</style>
