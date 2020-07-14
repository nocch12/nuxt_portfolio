<template>
  <div>
    <section class="hero is-dark is-medium hero-bg">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Kohki Ohno
          </h1>
          <h2 class="subtitle">
            Hero subtitle
          </h2>
        </div>
      </div>
    </section>
    <section class="section container">
      <div class="columns is-tablet is-centered">
        <div class="column is-half-tablet has-text-centered-tablet">
          <p>
            ブログ兼ポートフォリオサイトです。<br />
            よろしくお願いします。
          </p>
          <div class="has-text-right-mobile mt-15">
            <nuxt-link class="button is-primary" :to="{ name: 'profile' }">
              プロフィール
            </nuxt-link>
          </div>
        </div>
      </div>
    </section>
    <section class="section container">
      {{ posts }}
      <template v-if="posts.length">
        <ul class="columns is-multiline is-tablet">
          <li
            v-for="(post, i) in posts"
            :key="i"
            class="column is-one-third-tablet"
          >
            <post-card :post="post" />
            <span>{{ post.fields.body }}</span>
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
import client from '~/plugins/contentful'
import PostCard from '~/components/PostCard'
export default {
  name: 'HomePage',
  components: { PostCard },
  async asyncData({ env }) {
    let posts = []
    await client
      .getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        order: '-fields.publishDate',
      })
      .then((res) => (posts = res.items))
      .catch((err) => console.error(err))
    return { posts }
  },
}
</script>

<style lang="scss" scoped>
.hero-bg {
  background: linear-gradient(135deg, #121212 50%, rgba(18, 18, 18, 0.3)),
    url('/img/main_bg.jpg');
  background-size: cover;
  background-position: 100% 100%;
}
</style>
