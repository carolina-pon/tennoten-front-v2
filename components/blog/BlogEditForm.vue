<!-- 今後必要であればダイアログを別ファイルに切り出す。今は一緒くたにかいてる。 -->
<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6" md="6">
          <v-text-field label="記事タイトル"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="6">
          <v-textarea
            name="input-7-1"
            label="ブログ本文"
          ></v-textarea>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="6">
        <v-btn class="ma-2" outlined>投稿する</v-btn>
      </v-col>
    </v-row>
    </v-container>
  </v-form>
</template>
