<template>
  <div class="container">
    <!-- <img src="../../assets/map.jpg" alt /> -->
    <div class="map">
      <!-- <div class="p"></div> -->
      <!-- <div class="p1"></div> -->
      <div class="quan quan_1"></div>
      <div class="quan quan_2"></div>
      <div class="quan quan_3"></div>
      <div class="quan1 quan_4"></div>
      <div class="quan1 quan_5"></div>
      <div class="quan1 quan_6"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.map {
    /* width: 1903px; */
    /* height: 837px; */
    /* position: absoule; */
    /* left: 0; */
    /* top: 0; */
    width: 100%;
    height: 900px;
    background: url(../../assets/map.jpg) no-repeat center/cover;
}
img {
  /* display: block; */
  width: 100%;
  height: 100%;
}

.p {
  width: 8px;
  height: 8px;
  background-color: red;
  border-radius: 50%;
}
.quan {
  width: 8px;
  height: 8px;
  /* border: 1px solid yellow; */
  box-shadow: 0 0 10px red;
  border-radius: 50%;
  /* 居中解决 */
  position: absolute;
  top: 50%;
  left: 90%;
  transform: translate(-50%, -50%);
  /* 调用 */
  animation: fangda 1.2s linear infinite;
}
@keyframes fangda {
  0% {
    /* 变化之前，基于上一个状态 */
    /* 第一个方法 */
    width: 8px;
    height: 8px;
    /* transform: translate(-50%, -50%) scale(1);   */
    opacity: 0;
  }
  70% {
    /* transform: translate(-50%, -50%) scale(4);   */
    width: 30px;
    height: 30px;
    opacity: 1;
  }
  100% {
    /* transform: translate(-50%, -50%) scale(6);   */
    width: 50px;
    height: 50px;
    opacity: 0;
  }
}
.p1 {
  width: 8px;
  height: 8px;
  background-color: green;
  border-radius: 50%;
}
.quan1 {
  width: 8px;
  height: 8px;
  /* border: 1px solid yellow; */
  box-shadow: 0 0 10px red;
  border-radius: 50%;
  /* 居中解决 */
  position: absolute;
  top: 30%;
  left: 30%;
  transform: translate(-50%, -50%);
  /* 调用 */
  animation: fangda 1.2s linear infinite;
}

.quan_1 {
  animation-delay: 0s;
}
.quan_2 {
  animation-delay: 0.7s;
}
.quan_3 {
  animation-delay: 1.4s;
}

.quan_4 {
  animation-delay: 0s;
}
.quan_5 {
  animation-delay: 0.7s;
}
.quan_6 {
  animation-delay: 1.4s;
}
</style>
