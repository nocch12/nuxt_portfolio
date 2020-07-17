<template>
  <section class="container section">
    <h2 class="title is-3 mb-20">{{ currentPost.fields.title }}</h2>
    <img
      :src="setEyeCatch(currentPost).url"
      :alt="setEyeCatch(currentPost).title"
    />
    <span>{{ currentPost.fields.publishDate }}</span>
    <Breadcrumbs :add-items="breadcrumbs" />
    <div class="main-content">
      <div v-html="$md.render(currentPost.fields.body)"></div>
    </div>
  </section>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  async asyncData({ payload, store, params, error }) {
    const currentPost =
      payload ||
      (await store.state.posts.find((post) => post.fields.slug === params.slug))

    if (currentPost) {
      return {
        currentPost,
        category: currentPost.fields.category,
      }
    } else {
      return error({ statusCode: 400 })
    }
  },
  computed: {
    ...mapGetters(['setEyeCatch', 'linkTo']),
    breadcrumbs() {
      return [
        {
          name: this.category.fields.name,
          to: this.linkTo('categories', this.category),
        },
      ]
    },
  },
}
</script>
