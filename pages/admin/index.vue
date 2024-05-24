<script setup>
import { ref } from "vue";

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
</script>

<template>
  <v-app id="inspire">
    <v-app-bar flat title="管理画面">
      <v-container class="mx-auto d-flex align-center justify-center">
        <!-- <v-btn
          v-for="link in links"
          :key="link"
          :text="link"
          variant="text"
        ></v-btn> -->

        <v-spacer></v-spacer>

        <v-responsive max-width="160">
          <v-text-field
            density="compact"
            flat
            hide-details
            label="Search"
            rounded="lg"
            single-line
            variant="solo-filled"
          >
          </v-text-field>
        </v-responsive>
      </v-container>
    </v-app-bar>

    <v-main class="bg-grey-lighten-3">
      <v-container>
        <v-row>
          <v-col cols="2">
            <v-sheet rounded="lg">
              <v-list rounded="lg">
                <v-list-item link title="Admin Users"></v-list-item>
                <v-list-item
                  link
                  title="Authors"
                  @click="showAuthors"
                ></v-list-item>
                <v-list-item
                  link
                  title="Blogs"
                  @click="showBlogs"
                ></v-list-item>
                <v-list-item
                  link
                  title="Works(Archive)"
                  @click="showWorks"
                ></v-list-item>
                <v-list-item link title="Categories"></v-list-item>
              </v-list>
            </v-sheet>
          </v-col>

          <v-col>
            <v-sheet min-height="70vh" rounded="lg">
              <v-col>
                <v-list lines="one" v-if="showAuthorsList">
                  <v-list-item class="text-h5">Authors</v-list-item>
                  <v-list-item v-for="author in authors" :key="author.id">
                    {{ author.name }}
                    <v-btn flat class="ma-2" color="teal-lighten-2">
                      編集
                      <v-icon end icon="mdi-file-edit-outline"></v-icon>
                    </v-btn>
                    <v-btn flat class="ma-2" color="deep-orange-accent-2">
                      削除<v-icon end icon="mdi-delete-circle-outline"></v-icon>
                    </v-btn>
                  </v-list-item>
                </v-list>
              </v-col>
              <v-list lines="one" v-if="showBlogsList">
                <v-list-item class="text-h5">Blogs</v-list-item>
                <v-list-item v-for="blog in blogs" :key="blog.id">
                  <strong>Title:</strong>{{ blog.title }}
                  <strong>Author:</strong>{{ getAuthorName(blog.author_id) }}
                  <v-btn flat class="ma-2" color="teal-lighten-2">
                    編集
                    <v-icon end icon="mdi-file-edit-outline"></v-icon>
                  </v-btn>
                  <v-btn flat class="ma-2" color="deep-orange-accent-2">
                    削除<v-icon end icon="mdi-delete-circle-outline"></v-icon>
                  </v-btn>
                </v-list-item>
              </v-list>
              <v-list lines="one" v-if="showWorksList">
                <v-list-item class="text-h5">Works</v-list-item>
                <v-list-item v-for="work in works" :key="work.id">
                  <strong>Title:</strong>{{ work.title }}
                  <v-btn flat class="ma-2" color="teal-lighten-2">
                    編集
                    <v-icon end icon="mdi-file-edit-outline"></v-icon>
                  </v-btn>
                  <v-btn flat class="ma-2" color="deep-orange-accent-2">
                    削除<v-icon end icon="mdi-delete-circle-outline"></v-icon>
                  </v-btn>
                </v-list-item>
              </v-list>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
