<script setup>
// patchに変える
const postAuthor = async (authorName) => {
  const { data: post_authors } = await useFetch("http://localhost:3000/api/authors", {
    method: "POST",
    body: JSON.stringify({ name: authorName }),
    headers: {
      "Content-Type": "application/json",
    },
  });
  return post_authors;
};
</script>
<!-- 今後必要であればダイアログを別ファイルに切り出す。今は一緒くたにかいてる。 -->
<template>
  <v-row>
    <v-col cols="12" md="6">
      <v-text-field label="作者名" v-model="authorName"></v-text-field>
    </v-col>
  </v-row>
  <v-row>
    <v-col cols="12" md="6">
      <v-btn class="ma-2" outlined @click="postAuthor(authorName).then(() => authors.value.push({ name: authorName }))">投稿する</v-btn>
    </v-col>
  </v-row>
</template>

