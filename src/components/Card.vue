<template>
  <div class="card">
    <img :src="news.image" alt="Новость" class="hidden-alt"/>
    <div class="inner-card">
      <div class="date">
        <div class="day">
          {{ news.day }}
        </div>
        <div class="year-and-day">
          <div class="month">
          {{news.month}}
        </div>
          <div class="year">
            {{ news.year}}
          </div>
        </div>
      </div>
      <div class="name-link">{{ news.name }}</div>
      <div class="preview-text">{{ news.previewText }}</div>
      <div class="type-of-news">
        <div class="type-of-news-text">{{ news.type.value }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    news: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style scoped>
*{
  box-sizing: border-box;
}
*::before,*::after{
  box-sizing: inherit;
}
.card{
  width: 536px;
  height: 554px;
  align-items: flex-start;
  border-radius: 16px;
  border: 1px solid #0F62FE;
  position: relative;
}
.hidden-alt {
  color: transparent;
}
img{
  height: 250px;
  align-self: stretch;
  border-radius: 16px 16px 0px 0px;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 50% 50%;
}
.day{
  color: #A1A7B5;
  font-family: Nunito Sans,sans-serif;
  font-size: 36px;
  font-style: normal;
  font-weight: 400;
  line-height: 100%; /* 36px */
}
.year{
  color: #A1A7B5;
  font-family: Nunito Sans,sans-serif;
  font-size: 15px;
  font-style: normal;
  font-weight: 700;
  line-height: 110%; /* 16.5px */
  letter-spacing: -0.15px;
}
.month{
  color: #A1A7B5;
  font-family: Nunito Sans,sans-serif;
  font-size: 15px;
  font-style: normal;
  font-weight: 700;
  line-height: 110%; /* 16.5px */
  letter-spacing: -0.15px;
}
.date{
  display: flex;
  align-items: center;
  gap: 4px;
}
.name-link{
  align-self: stretch;
  color: #0C5BEF;
  font-family: Nunito Sans,sans-serif;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120%;
  margin-bottom: 16px;
}
.inner-card {
  margin: 32px;
}
.preview-text{
  align-self: stretch;
  color: #222327;
  font-family: Nunito Sans,sans-serif;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: 130%; /* 26px */
  letter-spacing: -0.2px;
}
.type-of-news {
  position: absolute;
  bottom: 32px;
  left: 32px;
  display: flex;
  padding: 4px 16px;
  justify-content: center;
  align-items: center;
  gap: 2px;
  border-radius: 360px;
  background: #F0F6FE;
  max-height: 28px;
}

.type-of-news-text {
  color: #00133A;
  font-family: Nunito Sans,sans-serif;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 140%;
}
</style>