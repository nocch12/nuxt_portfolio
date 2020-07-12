<template>
  <div>
    <div class="columns is-multiline has-text-centered">
      <div v-for="item in profile" :key="item.key" class="column is-4">
        <div class="card">
          <header class="card-header">
            <p class="card-header-title is-centered">
              <b-icon :icon="item.icon"></b-icon>
              <span class="card-header-title-text">{{ item.key }}</span>
            </p>
          </header>
          <div class="card-content">
            <div class="content">
              {{ item.value }}
            </div>
          </div>
        </div>
      </div>
      <div class="column is-12">
        <div class="card">
          <header class="card-header">
            <p class="card-header-title is-centered">
              <b-icon icon="pencil"></b-icon>
              <span class="card-header-title-text">その他</span>
            </p>
          </header>
          <div class="card-content">
            <div class="content">
              埼玉県某所で妻と二人暮らし。
              <br />
              暇なときは、PCをカタカタしたり、RPG系のゲームをやったりしています。
              <br />
              休日は、カラオケ、温泉、旅行に行きたい。（あまり行けてない）
              <br />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  data() {
    return {
      birthday: '1993-12-22',
    }
  },
  computed: {
    profile() {
      return [
        {
          icon: 'label',
          key: 'name',
          value: '大野 昂希',
        },
        {
          icon: 'airplane-takeoff',
          key: 'birthday',
          value: this.BDText,
        },
        {
          icon: 'briefcase',
          key: 'job',
          value: 'Webエンジニア',
        },
      ]
    },
    BDText() {
      const data = this.calcAge(this.birthday)

      return `${data.date} (年齢: ${data.age})`
    },
  },
  methods: {
    calcAge(date) {
      const birthday = moment(date)
      const today = moment()
      const birthdayThisYear = moment(date).set('year', today.year())

      let age = today.year() - birthday.year()

      if (today.isBefore(birthdayThisYear)) {
        age -= 1
      }

      return {
        date: birthday.format('YYYY/MM/DD'),
        age,
      }
    },
  },
}
</script>
