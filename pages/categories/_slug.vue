<template>
  <div class="section container">
    <Breadcrumbs :add-items="breadcrumbs" />
    {{ category.fields.name }}
    <section>
      <template v-if="posts.length">
        <ul>
          <li v-for="(post, i) in posts" :key="i" class="mb-20 is-block">
            <post-card :post="post" />
          </li>
        </ul>
      </template>
      <template v-else>
        投稿された記事はありません。
      </template>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ payload, store, params, error }) {
    const category =
      payload ||
      (await store.state.categories.find(
        (cat) => cat.fields.slug === params.slug
      ))

    if (category) {
      return { category }
    } else {
      return error({ statusCode: 400 })
    }
  },
  computed: {
    posts() {
      return this.$store.getters.relatedPosts(this.category)
    },
  },
}
</script>
