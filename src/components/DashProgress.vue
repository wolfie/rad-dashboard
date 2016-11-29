<template>
  <div>
    <div v-for="project in projects">
      <h1>{{ project.name }}</h1>
      <div class="wrapper">
        <ul>
          <li v-for="highlight in project.highlights">{{ highlight }}</li>
        </ul>
        <dash-progress-graph class="graph"
          :start="project.graphdata.start"
          :target="project.graphdata.target"
          :maybe="project.graphdata.maybe"
          :probably="project.graphdata.probably"></dash-progress-graph>
      </div>
    </div>
  </div>
</template>

<script>
  import DashProgressGraph from './DashProgressGraph'

  export default {
    name: 'dash-progress',
    components: {
      DashProgressGraph
    },
    data: function() { return {
      projects: [
        {
          name: 'Spreadsheet 1.3',
          highlights: [
            'Newer version of POI',
            'Support for named ranges',
            'Support for SUBTOTAL function'
          ],
          graphdata: {
            start: new Date('2016-05-01'),
            target: new Date('2017-12-01'),
            maybe: new Date('2017-11-01'),
            probably: new Date('2018-01-01')
          }
        },
        {
          name: 'Designer 1.1',
          highlights: [
            'IDEA support',
            'Customizable content in components',
            'Support variants of Eclipse',
            'HTML snippets'
          ],
          graphdata: {
            start: new Date('2016-05-01'),
            target: new Date('2017-12-01'),
            maybe: new Date('2017-11-01'),
            probably: new Date('2018-01-01')
          }
        }
      ]
    } }
  }
</script>

<style scoped>
  .wrapper {
    display: flex;
  }
  .graph {
    font-size: 80%
  }
</style>
