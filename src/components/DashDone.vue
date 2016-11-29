<template>
  <div>
    <div v-for="team in teams">
      <h2>{{ team.name }}</h2>
      <div v-for="release in team.releases" class="row">
        <div>{{ release.date }}</div>
        <div>{{ release.name }}</div>
        <ul>
          <li v-for="note in release.notes">{{ note }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'dash-done',
    data: function() { return {
      teams: [
        {
          name: 'Elements',
          releases: [
            {
              date: '2016-11-25',
              name: 'vaadin-foo 2.0',
              notes: [
                '100% increase of bazzing',
                'Ipsum dolor',
                'Sit amet'
              ]
            },
            {
              date: '2016-11-23',
              name: 'vaadin-fizz-buzz 1.2 alpha 1',
              notes: [
                'Sit amet',
                'Ipsum dolor'
              ]
            }
          ]
        }
      ]
    } }
  }
</script>

<style scoped>
</style>
