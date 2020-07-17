<template>
  <nav class="breadcrumb" aria-label="breadcrumbs">
    <ul>
      <li v-for="item in items" :key="item.name">
        <nuxt-link :to="item.to">{{ item.name }}</nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    items: {
      type: Object,
      required: true,
    },
  },
}
</script>
