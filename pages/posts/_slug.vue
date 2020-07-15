<template>
  <div>
    <img
      :src="setEyeCatch(currentPost).url"
      :alt="setEyeCatch(currentPost).title"
    />
    <span>{{ currentPost.fields.title }}</span>
    <span>{{ currentPost.fields.publishDate }}</span>
    <span>{{ currentPost.fields.body }}</span>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import client from '~/plugins/contentful'

export default {
  async asyncData({ env, params }) {
    let currentPost = null
    await client
      .getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        'fields.slug': params.slug,
      })
      .then((res) => (currentPost = res.items[0]))
      .catch((err) => console.error(err))

    return { currentPost }
  },
  computed: {
    ...mapGetters(['setEyeCatch']),
  },
}
</script>
