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
import { mapState } from 'vuex'
import PostCard from '~/components/PostCard'

export default {
  name: 'HomePage',
  components: { PostCard },
  computed: {
    ...mapState(['posts']),
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
