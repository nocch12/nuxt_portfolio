<template>
  <div>
    <div class="columns is-multiline has-text-centered">
      <div v-for="item in items" :key="item.lang" class="column is-4">
        <div class="card">
          <header class="card-header">
            <p class="card-header-title is-centered">
              <b-icon :icon="item.icon"></b-icon>
              <span class="card-header-title-text">{{ item.lang }}</span>
            </p>
          </header>
          <div class="card-content">
            <div class="content">
              {{ item.text }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          icon: 'language-html5',
          lang: 'HTML',
          text: '経験: 約1年',
        },
        {
          icon: 'language-css3',
          lang: 'CSS',
          text: '経験: 約1年',
        },
        {
          icon: 'language-javascript',
          lang: 'JavaScript',
          text: '経験: 約1年',
        },
        {
          icon: 'vuejs',
          lang: 'Vue.js',
          text: '経験: 半年',
        },
        {
          icon: 'language-php',
          lang: 'PHP',
          text: '経験: 約1年',
        },
        {
          icon: 'laravel',
          lang: 'Laravel',
          text: '経験: 約1年',
        },
      ],
    }
  },
}
</script>
