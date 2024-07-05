<template>
  <v-app class="flex-grow-0">
    <v-app-bar
      app
      color="secondary"
      dark
    >
      <v-app-bar-title>
        <h6 class="text-h6 white--text d-none d-sm-flex">Text Tags</h6>
      </v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn
        href="https://hh.ru/resume/1e69b519ff0ccc218b0039ed1f6e4633786834"
        target="_blank"
        text
      >
        <span class="mr-2">Applicant's HH</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <div class="d-flex flex-wrap">
        <TagList :tags="tags" />
        <TagList :tags="tags" isStretched/>
        <TagList :tags="tags" isHalfWidth />
        <TagList :tags="tags" isHalfWidth isStretched />
      </div>
    </v-main>

  </v-app>
</template>

<script>
import TagList from '@/components/TagList';
import { TAG_LIST } from '@/mocked-data/tags.js'

export default {
  name: 'App',
  components: {
    TagList,
  },
  data() {
    return {
      tags: TAG_LIST,
    }
  },
};
</script>
