<template>
  <div class="news-section">
    <transition name="fade-in" appear>
      <div class="news-title" v-if="show">
        <span class="en-bg">NEWS</span>
        <div class="zh-row">
          <span class="line"></span>
          <span class="zh">新闻动态</span>
        </div>
        <button class="more-btn">查看更多 &gt;</button>
      </div>
    </transition>
    <div class="news-cards">
      <div class="news-card big">
        <img :src="cards[0].img" :alt="cards[0].title" />
        <div class="news-info">
          <div class="news-main-title">{{ cards[0].title }}</div>
          <div v-if="cards[0].desc" class="news-desc">{{ cards[0].desc }}</div>
          <div class="news-date">{{ cards[0].date }}</div>
        </div>
      </div>
      <div class="right-cards">
        <div class="news-card small">
          <img :src="cards[1].img" :alt="cards[1].title" />
          <div class="news-info">
            <div class="news-main-title">{{ cards[1].title }}</div>
            <div class="news-date">{{ cards[1].date }}</div>
          </div>
        </div>
        <div class="news-card small">
          <img :src="cards[2].img" :alt="cards[2].title" />
          <div class="news-info">
            <div class="news-main-title">{{ cards[2].title }}</div>
            <div class="news-date">{{ cards[2].date }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import banner1 from '../assets/news_section.png'
import banner2 from '../assets/news_people1.jpg'
import banner3 from '../assets/news_people2.webp'

const show = ref(false)
onMounted(() => {
  setTimeout(() => {
    show.value = true
  }, 100)
})

const cards = [
  {
    img: banner1,
    size: 'big',
    title: '福耀科技大学正式获教育部批准设立',
    desc: '聚焦“高起点、小而精、研究型、国际化”的办学方向，努力探索出一条为党育人、为国育才的新型研究型大学创新发展之路。',
    date: '2025.03.11'
  },
  {
    img: banner2,
    size: 'small',
    title: '香港城市大学校长梅彦昌院士一行来访福耀科技大学',
    date: '2025.07.07'
  },
  {
    img: banner3,
    size: 'small',
    title: '史太白技术管理中国总部一行来访福耀科技大学洽谈合作',
    date: '2025.06.23'
  }
]
</script>

<style scoped>
.news-section {
  width: 100vw;
  height: 45vw;
  background: #fafbfc;
  padding: 40px 0 60px 0;
  position: relative;
  overflow: hidden;
}
.news-section::before {
  content: "";
  position: absolute;
  left: 0; top: 0; right: 0; bottom: 0;
  background: url('../assets/news_section-bg.png') center/cover no-repeat;
  opacity: 1;
  z-index: 0;
  pointer-events: none;
}
.news-title {
  position: relative;
  margin-left: 80px;
  margin-bottom: 24px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  height: 110px;
  justify-content: flex-end;
}
.en-bg {
  position: absolute;
  top: 0;
  left: 0;
  font-size: 4.5rem;
  color: #ededed;
  font-style: italic;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  letter-spacing: 0.1em;
  z-index: 0;
  user-select: none;
  pointer-events: none;
}
.zh-row {
  display: flex;
  align-items: center;
  position: relative;
  z-index: 1;
}
.line {
  display: inline-block;
  width: 260px;
  height: 3px;
  background: #f7931e;
  margin-right: 18px;
  border-radius: 2px;
}
.zh {
  color: #f7931e;
  font-size: 2.6rem;
  font-weight: bold;
  line-height: 1.1;
}
.more-btn {
  position: absolute;
  right: 190px;
  top: 50%;
  transform: translateY(-20%);
  padding: 8px 24px;
  border: 1px solid #888;
  border-radius: 24px;
  background: #fff;
  color: #333;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.2s;
}
.more-btn:hover {
  background: #f7931e;
  color: #fff;
  border-color: #f7931e;
}
.news-cards {
  display: flex;
  gap: 24px;
  max-width: 1100px;
  margin: 0 auto;
  align-items: stretch;
}
.news-card.big {
  flex: 1 1 0;
  height: 480px;
}
.news-card.big .news-info {
  background: rgba(145,108,92,0.67);
}
.news-card.small .news-info {
  background: rgba(0,0,0,0.5);
}
.right-cards {
  display: flex;
  flex-direction: column;
  flex: 1 1 0;
  height: 480px;
  gap: 16px;
}
.news-card.small {
  flex: 1 1 0;
  height: 50%;
  margin: 0;
}
.news-card {
  background: transparent;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 24px rgba(0,0,0,0.08);
  display: flex;
  flex-direction: column;
  transition: box-shadow 0.2s, opacity 1, transform 0.7s;
  opacity: 1;
  z-index: 1000;
}
.news-card img {
  width: 100%;
  height: 65%;
  object-fit: cover;
}
.news-info {
  padding: 12px 16px 8px 16px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  height: 35%;
}
.news-main-title {
  font-size: 1.1rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 8px;
  line-height: 1.3;
}
.news-desc {
  font-size: 0.95rem;
  color: #888;
  margin-bottom: 8px;
}
.news-date {
  font-size: 0.9rem;
  color: #bdbdbd;
  margin-top: auto;
}
@media (max-width: 1100px) {
  .news-cards {
    flex-direction: column;
    align-items: center;
    max-width: 98vw;
  }
  .news-card.big, .right-cards {
    width: 90vw;
    max-width: 800px;
    height: auto;
  }
  .right-cards {
    flex-direction: row;
    height: auto;
  }
  .news-card.small {
    height: auto;
  }
}

.fade-in-enter-active {
  transition: opacity 0.7s cubic-bezier(.4,0,.2,1), transform 0.7s cubic-bezier(.4,0,.2,1);
}
.fade-in-enter-from {
  opacity: 0;
  transform: translateY(40px);
}
.fade-in-enter-to {
  opacity: 1;
  transform: translateY(0);
}
</style> 