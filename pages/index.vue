<script setup lang="ts">
// 旧実装
// const { fetchArticles, articles } = useArticles();
// fetchArticles();

// userFetch($fetch)利用
const { data: articles, refresh } = useFetch('/api/blogs');
</script>

<template>
  <div>
    <p>新着記事！！</p>
    <ul>
      <li v-for="article in articles" :key="article.id">
        <NuxtLink :to="{path: '/details', query: { id: article.id }}">{{
            article.title
          }}
        </NuxtLink>
      </li>
    </ul>

    <!-- データ更新処理 -->
    <button @click="refresh">最新情報取得</button>
    <Advertisement />
  </div>
</template>
