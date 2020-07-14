<template>
  <section class="container section">
    <b-tabs type="is-toggle" expanded>
      <template v-for="tab in tabs">
        <b-tab-item :key="tab.label" :label="tab.label">
          <component :is="tab.component" />
        </b-tab-item>
      </template>
    </b-tabs>
  </section>
</template>

<script>
import AboutPage from '@/components/templates/AboutPage'
import SkillsPage from '@/components/templates/SkillsPage'
import WorksPage from '@/components/templates/WorksPage'

export default {
  components: {
    AboutPage,
    SkillsPage,
    WorksPage,
  },
  data() {
    return {
      activeTab: 0,
      showMusic: true,
      showBooks: false,
      multiline: true,
      tabs: [
        {
          label: 'About',
          component: AboutPage,
          displayed: true,
        },
        {
          label: 'Skills',
          component: SkillsPage,
          displayed: true,
        },
        {
          label: 'Works',
          component: WorksPage,
          displayed: true,
        },
      ],
    }
  },
}
</script>

<style lang="scss">
.card-header-title-text {
  margin-left: 0.6rem;
}
</style>
