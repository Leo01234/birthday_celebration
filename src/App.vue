<script setup>
import BirthdayCake from './components/BirthdayCake.vue'
import CelebrationAnimation from './components/CelebrationAnimation.vue'

// One day Time in ms (milliseconds)
let one_day = 1000 * 60 * 60 * 24;

// To set present_dates to two variables
let present_date = new Date();

// 0-11 is Month in JavaScript
let birth_date = new Date(2006, 3, 8);
let next_birth_date = new Date(present_date.getFullYear(), 3, 8);

let age = present_date.getFullYear() - birth_date.getFullYear();
let m = present_date.getMonth() - birth_date.getMonth();
let d = present_date.getDate() - birth_date.getDate();

// To Calculate next year's birthday if passed already.
if (m > 0 || (m === 0 && d > 0)) {
		next_birth_date.setFullYear(next_birth_date.getFullYear() + 1);
}
if (m < 0 || (m === 0 && d < 0)) {
    age--;
}

// To Calculate the result in milliseconds and 
// then converting into days
let days_remaining = Math.ceil((next_birth_date.getTime() - present_date.getTime()) / one_day);

// To remove the decimals from the (days_remaining) 
// resulting days value
let s_days_remaining = days_remaining.toFixed(0);

let title = '';
let content = '';

if (days_remaining === 0) {
  title = `祝槐序<br/>${age}岁生日快乐`;
  switch (age) {
    case 18:
      content = '恭喜成年！祝愿你在新的一岁里，<br/>独立自主，积极进取！';
      break;
    case 19:
      content = '祝你找到人生的目标！';
      break;
    case 20:
      content = '祝你寻到自己的幸福！';
      break;
    case 21:
      content = '祝你实现自己的梦想！';
      break;
    default:
      content = '许个愿吧！';
  }
  if (age > 150) {
    content = '你是怎么活这么久的？<br/>快告诉我！';
  }
} else {
  title = `你已经${age}岁了哦`;
  content = `槐序距离下一次生日<br/>还有${s_days_remaining}天`;
}

</script>

<template>
  <h1 class="title" v-html="title"></h1>
  <BirthdayCake />
  <CelebrationAnimation />
  <div class="footer">
    <div class="content" v-html="content"></div>
    <div class="tip">轻触熄灭蜡烛 | 页面根据日期变化，明年再来看看吧</div>
  </div>
</template>

<style scoped>
  .title {
    position: absolute;
    width: 100%;
    text-align: center;
    font-weight: bold;
    font-size: 64px;
    background: -webkit-linear-gradient(90deg, #ff6f82 50%, #ff64e5);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .footer {
    position: absolute;
    bottom: 0;
    width: 100%;
    text-align: center;
  }
  .content {
    font-size: 30px;
    margin-bottom: 60px;
    color: #e52cab;
  }
  .tip {
    color: gray;
  }
</style>
