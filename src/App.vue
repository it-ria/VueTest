<template>
  <div class="q-pa-md row justify-center q-gutter-md">
    <news-card-vue
      v-for="(article, index) in articles"
      :key="index"
      :article="article"
    />
    
  </div>
</template>

<script>
import axios from "axios";
import NewsCardVue from "./components/NewsCard.vue";

export default {
  components: {
    // HelloWorld
    NewsCardVue,
  },
  data() {
    return {
      data: "aref",
      info: null,
      articles: [],
    };
  },
  mounted() {
    let config = {
      headers: {
        "x-api-key": "07265249548748a686491cba77761458",
      },
    };
    axios
      .get("https://newsapi.org/v2/everything?q=khamenei", config)
      .then((response) => {
        this.articles = response.data.articles;
        console.log(response.data);
      });
  },
};
</script>
