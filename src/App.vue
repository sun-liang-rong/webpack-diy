<template>
  <!-- <div>
    <div class="box">
      <img src="@/assets/images/1.png" alt="" />
    </div>
  </div> -->
  <div>
    211111
    <div class="record">
      <div v-for="(item, index) in list" :key="index" class="item border">
        <div
          v-for="(v, indexs) in 10"
          :key="indexs"
          class="item"
          :style="{ ...style(item) }"
        >
          {{ indexs }}
        </div>
      </div>
    </div>

    <div
      @click="randomNumber"
      style="width: 850px; height: 100px; background: #ccc; margin-top: 100px"
    >
      0000
    </div>
  </div>
</template>
<script setup>
import { ref, computed, watch } from "vue";
// export default {
// data() {
// return {
// 父级传入
const quantity = ref(9); //默认9个
const delayed = ref(true); //从零变化
const number = ref("123456789"); //数字
const time = ref(2000); //过度时间
const timing = ref("ease"); //过度动画速度
const num = ref(0);
const numArr = computed(() => {
  if (num.value) {
    return (num.value + "").split("");
  } else {
    return new Array(number.value.length).fill(0);
  }
});
const list = computed(() => {
  let arr = [];
  let len = numArr.value.length;
  if (quantity.value && quantity.value > len) {
    arr = [...new Array(quantity.value - len).fill(0), ...numArr.value];
  } else {
    arr = numArr.value;
  }
  console.log(arr, '----------')
  return arr;
});
const randomNumber = () => {
  number.value = "1000000"; //Math.floor(Math.random() * (999999999 - 1 + 1)) + 1
};
const style = (e) => {
  console.log(e, '-==========');
  console.log({
    transform: `translateY(-${e * 100}%)`,
    transition: time.value + "ms",
    transitionTimingFunction: timing.value,
  })
  return {
    transform: `translateY(-${e * 100}%)`,
    transition: time.value + "ms",
    transitionTimingFunction: timing.value,
  };
};

if (delayed.value) {
  setInterval(() => {
    num.value = Math.floor(Math.random() * (999999999 - 1 + 1)) + 1;
  }, 3000);
} else {
  num.value = number.value;
}
watch(number, (newValue, oldValue) => {
  // 	//newValue 新的值，oldValue变化前的值
  num.value = newValue;
  // }
});
</script>
<style lang="less" scoped>
* {
  touch-action: pan-y;
}
.record {
  display: flex;
  padding-top: 100px;
  width: 100%;
  align-items: center;
  justify-content: center;
}
.item {
  width: 60px;
  height: 80px;
  font-size: 50px;
  color: rgb(109, 160, 255);
  font-weight: 600;
  margin-right: 20px;
  text-align: center;
  line-height: 80px;
  overflow: hidden;
}
.border {
  border: 1px solid #ccc;
}
</style>
<!-- <script setup>
import { ref } from "vue";
</script>

<style lang="less" scoped>
@import './App.less';
</style> -->
