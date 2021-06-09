<template>
  <div v-for="article in news" v-bind:key="article">
    <div
      class="h-40 bg-gray-100 mt-3"
      :style="{
        backgroundImage: `url(${article.img})`,
        backgroundSize: `cover`,
      }"
      v-if="article.img"
    >
      <div
        class="flex items-end w-full h-full"
        style="background-color: rgba(0, 0, 0, 0.6)"
      >
        <div class="px-4 py-2">
          <div class="text-sm text-green-400 mb-2">{{ article.source }}</div>
          <div class="mb-2">
            <a
              :href="article.url"
              class="
                font-semibold
                leading-tight
                text-xl text-gray-100
                hover:text-gray-100
                hover:underline
              "
              target="_blank"
            >
              {{ article.title }}
            </a>
          </div>
          <div class="flex text-gray-200 text-sm">
            <div class="pr-3">{{ article.published }}</div>
            <div>{{ article.author }}</div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="w-full h-40 bg-gray-100 mt-3"
      :style="{
        background: `linear-gradient(90deg, rgba(36,1,97,1) 0%, rgba(78,9,121,1) 35%, rgba(0,212,255,1) 79%)`,
      }"
      v-else
    >
      <div
        class="flex items-end h-full"
        style="background-color: rgba(0, 0, 0, 0.6)"
      >
        <div class="px-4 py-2">
          <div class="text-sm text-green-400 mb-2">{{ article.source }}</div>
          <div class="mb-2">
            <a
              :href="article.url"
              class="
                font-semibold
                leading-tight
                text-xl text-gray-100
                hover:text-gray-100
                hover:underline
              "
              target="_blank"
            >
              {{ article.title }}
            </a>
          </div>
          <div class="flex text-gray-200 text-sm">
            <div class="pr-3">{{ article.published }}</div>
            <div>{{ article.author }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Articles",
  data() {
    return {
      message: "Hello",
      news: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://newsapi.org/v2/top-headlines?country=us&category=technology&apiKey=6a3a99ba97fd40fa956e37e15b727ef8"
      )
      .then((response) => {
        let date = new Date();
        let articles = response.data.articles;
        for (var i = 0; i < articles.length; i++) {
          let articleData = {
            title: articles[i].title,
            author: articles[i].author,
            desc: articles[i].description,
            img: articles[i].urlToImage,
            url: articles[i].url,
            source: articles[i].source.name,
            published: date.toDateString(articles[i].publishedAt),
          };
          this.news.push(articleData);
        }
      });
  },
};
</script>
<style></style>
