<template>
  <div>
    <div class="hero">
      <div class="news-text">Новости</div>
    </div>
    <div class="wrapper">
      <cards-list :newsItems="displayedNews"></cards-list>
      <div class="load-more">
        <button v-if="showLoadMoreButton"  @click="loadMore">Загрузить еще</button>
      </div>
    </div>
  </div>

</template>

<script>
import { ref, computed } from "vue";
import moment from "moment";

import CardsList from "../components/CardsList.vue";

export default {
  name: "NewsList",
  components: {
    CardsList,
  },
  setup() {
    const newsList = ref([]);
    const displayedNews = ref([]);

    const loadNews = async () => {
      const url = "https://flems.github.io/test/api/news/";
      try {
        const response = await fetch(url);
        const newsData = await response.json();

        newsData.items.forEach((newsItem) => {
          newsItem.day = moment(newsItem.date).format("DD");
          newsItem.month = moment(newsItem.date).format("MMMM");
          newsItem.year = moment(newsItem.date).format("YYYY");
        });

        newsList.value = newsData.items;
        displayedNews.value = newsList.value.slice(0, 9);
      } catch (error) {
        console.error(error);
      }
    };

    const loadMore = async () => {
      const nextPage = Math.ceil((displayedNews.value.length + 1) / 10) + 1;

      try {
        const url = `https://flems.github.io/test/api/news/${nextPage}/`;
        const response = await fetch(url);
        const newsData = await response.json();

        newsData.items.forEach((newsItem) => {
          newsItem.date = moment(newsItem.date).format("DD.MM.YYYY");
        });

        newsList.value = [...newsList.value, ...newsData.items];
        displayedNews.value = newsList.value.slice(0, displayedNews.value.length + 10);
      } catch (error) {
        console.error(error);
      }
    };

    loadNews();

    return {
      displayedNews,
      showLoadMoreButton: computed(() => displayedNews.value.length < newsList.value.length),
      loadMore,
    };
  },
};
</script>

<style scoped>
.load-more{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 72px;
}
.wrapper {
  max-width: 1710px;
  margin: 0 auto;
}

.hero {
  position: relative;
  width:100%;
  height: 320px;
  margin-bottom: 68px;
  background-image: url("../assets/headerImage.png");
  background-repeat: no-repeat;
  background-size: cover;
}

.news-text {
  position: absolute;
  bottom: 48px;
  left: 100px;
  display: flex;
  color: #17171A;
  font-family: Nunito Sans,sans-serif;
  font-size: 40px;
  font-style: normal;
  font-weight: 700;
  line-height: 120%; /* 48px */
  letter-spacing: -0.4px;
}
button{
  display: flex;
  padding: 16px 32px;
  justify-content: center;
  align-items: center;
  gap: 8px;
  border-radius: 8px;
  border: 1px solid #002DBF;
  background-color: white;
  color: #002DBF;
  text-align: center;
  font-family: Nunito Sans,sans-serif;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: 120%;
  letter-spacing: -0.2px;
}
button:hover {
  cursor: pointer;
}
</style>