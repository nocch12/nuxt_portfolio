<template>
  <header>
    <b-navbar shadow>
      <template slot="brand">
        <b-navbar-item tag="router-link" :to="{ path: '/' }">
          <h1>Kohki Ohno</h1>
        </b-navbar-item>
      </template>

      <template slot="end">
        <b-navbar-item tag="div">
          <ul class="menu-list is-flex-tablet">
            <li v-for="(item, key) of items" :key="key">
              <nuxt-link class="is-block" :to="item.to">
                {{ item.title }}
              </nuxt-link>
            </li>
          </ul>
        </b-navbar-item>
      </template>
    </b-navbar>
  </header>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' },
        },
        {
          title: 'profile',
          icon: 'lightbulb',
          to: { name: 'profile' },
        },
        {
          title: 'blog',
          icon: 'lightbulb',
          to: { name: 'blog' },
        },
      ],
    }
  },
}
</script>
