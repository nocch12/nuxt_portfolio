<template>
  <nuxt-link :to="linkTo" class="card is-block">
    <div class="card-image">
      <figure class="image is-4by3">
        <img :src="setEyeCatch(post).url" :alt="setEyeCatch(post).title" />
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-size-5-mobile is-size-4-tablet">
            {{ post.fields.title }}
          </p>
        </div>
      </div>

      <div class="content">
        <br />
        <time datetime="2016-1-1">{{ publishDate }}</time>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  computed: {
    ...mapGetters(['setEyeCatch']),
    publishDate() {
      return this.post.fields.publishDate
    },
    imageSrc() {
      if (this.post.fields.image) return this.post.fields.image.fields.file.url
      else return 'https://bulma.io/images/placeholders/1280x960.png'
    },
    linkTo() {
      return { name: 'posts-slug', params: { slug: this.post.fields.slug } }
    },
  },
}
</script>

<style lang="scss" scoped>
@media screen and(min-width: 769px) {
  .card {
    display: flex;
  }

  .card-image {
    width: 200px;
  }
}
</style>
