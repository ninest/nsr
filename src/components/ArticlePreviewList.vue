<script>
export default {
  props: {
    articles: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      tags: {},
      colors: {}
    }
  },
  async fetch() {
    const tags = (await this.$content('tags').fetch()).tags
    this.tags = tags
    
    // keys are the slugs
    const keys = Object.keys(tags);

    for (var i = 0; i < keys.length; i++) {
      const tagSlug = keys[i]
      this.colors[tagSlug] = tags[tagSlug].color
    }
  }
}
</script>

<template>
  <div class="article-list">
    <div v-if="$fetchState.pending">Loading articles ...</div>
    <ArticlePreview 
      v-else
      v-for="article in articles" v-bind:key="article.slug"
      :title="article.title"
      :slug="article.slug"
      :date="article.created"
      :tags="article.tags"
      :colors="colors"

      :tagsObject="tags"
    > 
    </ArticlePreview>
  </div>
</template>

<style lang="scss" scoped>
.article-list {
  // spacing between articles above/below each other
  a + a {
    margin-top: 1.2rem;
  }
}
</style>