<script setup>
import { ref } from "vue";
definePageMeta({ layout: "admin" });

const links = ref(["Dashboard", "Messages", "Profile", "Updates"]);
const { data: authors } = await useFetch("http://localhost:3000/api/authors");
const { data: blogs } = await useFetch("http://localhost:3000/api/blogs");
const { data: works } = await useFetch("http://localhost:3000/api/works");
const showAuthorsList = ref(false);
const showBlogsList = ref(false);
const showWorksList = ref(false);

const showAuthors = () => {
  showAuthorsList.value = true;
  showBlogsList.value = false;
  showWorksList.value = false;
};

const showBlogs = () => {
  showBlogsList.value = true;
  showAuthorsList.value = false;
  showWorksList.value = false;
};

const getAuthorName = (authorId) => {
  const author = authors.value.find((author) => author.id === authorId);
  return author ? author.name : "";
};

const showWorks = () => {
  showWorksList.value = true;
  showAuthorsList.value = false;
  showBlogsList.value = false;
};

const authorTableHeaders = [
  { title: "名前", key: "name" },
  { title: "拠点", key: "site" },
  { title: "SNS", key: "sns" },
  { title: "操作" },
];
const authorTableItems = authors.value.map((author) => ({
  name: author.name,
  site: author.site,
  sns: author.sns,
}));

const blogTableHeaders = [
  { title: "記事タイトル", key: "title" },
  { title: "名前", key: "name" },
  { title: "操作" },
];
const blogTableItems = blogs.value.map((blog) => ({
  title: blog.title,
  name: getAuthorName(blog.authorId),
}));

const workTableHeaders = [
  { title: "作品タイトル", key: "title" },
  { title: "作者", key: "author" },
  { title: "操作" },
];

const workTableItems = works.value.map((work) => ({
  title: work.title,
  author: getAuthorName(work.authorId),
}));
</script>

<template>
  <div class="bg-grey-lighten-3 pt-10 pb-10">
  <v-container class="pb-10">
    <v-row>
      <v-col cols="2">
        <v-sheet rounded="lg">
          <v-list rounded="lg">
            <v-list-item link title="サイト管理者" disabled></v-list-item>
            <v-list-item
              link
              title="作品制作者"
              @click="showAuthors"
            ></v-list-item>
            <v-list-item
              link
              title="制作ブログ"
              @click="showBlogs"
            ></v-list-item>
            <v-list-item
              link
              title="作品アーカイブ"
              @click="showWorks"
            ></v-list-item>
            <v-list-item link title="作品カテゴリー" disabled></v-list-item>
          </v-list>
        </v-sheet>
      </v-col>

      <v-col>
        <v-sheet min-height="70vh" rounded="lg">
          <v-list rounded="lg">
            <!-- 作品制作者一覧 -->
            <v-list lines="one" v-if="showAuthorsList">
              <v-list-item class="text-h5"
                >作品制作者一覧
                <v-btn
                  flat
                  class="ma-2"
                  color="teal-lighten-2"
                  @click="dialog = true"
                >
                  投稿
                </v-btn>
              </v-list-item>
              <v-divider></v-divider>
              <v-data-table
                :headers="authorTableHeaders"
                :items="authorTableItems"
              >
                <template v-slot:item="{ item }">
                  <tr>
                    <td>{{ item.name }}</td>
                    <td>{{ item.site }}</td>
                    <td>{{ item.sns }}</td>
                    <td>
                      <v-btn
                        flat
                        class="ma-2"
                        color="teal-lighten-2"
                        @click="editAuthors(author)"
                      >
                        編集
                      </v-btn>
                      <v-btn flat class="ma-2" color="deep-orange-accent-2">
                        削除
                      </v-btn>
                    </td>
                  </tr>
                </template>
              </v-data-table>
            </v-list>

            <!-- 制作ブログ一覧 -->
            <v-list lines="one" v-if="showBlogsList">
              <v-list-item class="text-h5"
                >制作ブログ一覧
                <v-btn flat class="ma-2" color="teal-lighten-2" @click="">
                  投稿
                </v-btn></v-list-item
              >
              <v-divider></v-divider>
              <v-data-table :headers="blogTableHeaders" :items="blogTableItems">
                <template v-slot:item="{ item }">
                  <tr>
                    <td>{{ item.title }}</td>
                    <!-- 作者表示されない。。。。修正必要 -->
                    <td>{{ item.name }}</td>
                    <td>
                      <v-btn
                        flat
                        class="ma-2"
                        color="teal-lighten-2"
                        @click="editAuthors(author)"
                      >
                        編集
                      </v-btn>
                      <v-btn flat class="ma-2" color="deep-orange-accent-2">
                        削除
                      </v-btn>
                    </td>
                  </tr>
                </template>
              </v-data-table>
            </v-list>

            <!-- 作品アーカイブ一覧 -->
            <v-list lines="one" v-if="showWorksList">
              <v-list-item class="text-h5"
                >制作アーカイブ一覧
                <v-btn flat class="ma-2" color="teal-lighten-2" @click="">
                  投稿
                </v-btn></v-list-item
              >
              <v-divider></v-divider>
              <v-data-table :headers="workTableHeaders" :items="workTableItems">
                <template v-slot:item="{ item }">
                  <tr>
                    <td>{{ item.title }}</td>
                    <!-- 作者表示されない。。。。修正必要 -->
                    <td>{{ item.name }}</td>
                    <td>
                      <v-btn flat class="ma-2" color="teal-lighten-2" @click="">
                        編集
                      </v-btn>
                      <v-btn flat class="ma-2" color="deep-orange-accent-2">
                        削除
                      </v-btn>
                    </td>
                  </tr>
                </template>
              </v-data-table>
            </v-list>
          </v-list>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</div>
</template>
