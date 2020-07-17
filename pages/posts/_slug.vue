<template>
  <section class="container section">
    <h2 class="title is-3 mb-20">{{ currentPost.fields.title }}</h2>
    <img
      :src="setEyeCatch(currentPost).url"
      :alt="setEyeCatch(currentPost).title"
    />
    <span>{{ currentPost.fields.publishDate }}</span>
    <bread-crumbs :items="breadcrumbs" />
    <div class="main-content">
      <div v-html="$md.render(currentPost.fields.body)"></div>
    </div>
  </section>
</template>

<script>
import { mapGetters } from 'vuex'
import BreadCrumbs from '~/components/BreadCrumbs'

export default {
  components: { BreadCrumbs },
  async asyncData({ payload, store, params, error }) {
    const currentPost =
      payload ||
      (await store.state.posts.find((post) => post.fields.slug === params.slug))

    if (currentPost) {
      return { currentPost }
    } else {
      return error({ statusCode: 400 })
    }
  },
  computed: {
    ...mapGetters(['setEyeCatch']),
    breadcrumbs() {
      const category = this.currentPost.fields.category
      return [
        { name: 'ホーム', to: '/' },
        { name: category.fields.name, to: '#' },
      ]
    },
  },
}
</script>
