<template>
  <nav class="breadcrumb" aria-label="breadcrumbs">
    <ul>
      <li v-for="item in breadcrumbs" :key="item.name">
        <nuxt-link :to="item.to">{{ item.name }}</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    addItems: {
      type: Array,
      default() {
        return []
      },
    },
  },
  data() {
    return {
      items: [{ name: 'ホーム', to: '/' }],
    }
  },
  computed: {
    breadcrumbs() {
      return this.items.concat(this.addItems)
    },
  },
}
</script>
