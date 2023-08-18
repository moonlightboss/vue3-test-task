<template>
  <div class="cards-list">
    <card v-for="newsItem in newsItems" :key="newsItem.id" :news="newsItem"></card>
  </div>
</template>


<script>
import Card from "./Card.vue";

export default {
  name: "CardsList",
  components: {
    Card
  },
  props: {
    newsItems: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.cards-list {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  gap: 48px;
}

card {
  flex: 0 0 calc(33.33% - 16px);
}
</style>