<script setup lang="ts">
const route = useRoute();
const { id }  = route.params;
//旧実装
// const { article, fetchArticle } = useArticles();
// fetchArticle(+id);

// useFetch($fetch)利用
const { data: article } = useFetch(`/api/blogs/${id}`);
</script>

<template>
  <div>
    <article v-if="article">
      <p>タイトル：{{ article.title }}</p>
      <hr />
      <div style="width: 500px">{{ article.content }}</div>
    </article>
    <NuxtLink to="/">戻る</NuxtLink>

    <Advertisement />
  </div>
</template>
