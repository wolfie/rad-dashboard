<template>
  <div class="support">
    <div v-for="(support, team) in supports" class="team">
      <h1>{{ team }}: {{ support.name }}</h1>
      <ul>
        <li v-for="(info, platform) in support.info">{{ platform }}: {{ info }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'dash-support',
    data: function() { return {
      supports: {
        'Framework': {
          name: 'John Smith',
          info: {
            Skype: 'jsmith',
            Flowdock: '#framework-support',
            Slack: '#framework-support'
          }
        },
        'Elements': {
          name: 'John Smith',
          info: {
            Skype: 'jsmith',
            Flowdock: '#framework-support',
            Slack: '#framework-support'
          }
        }
      }
    } }
  }
</script>

<style scoped>
  .support {
    display: flex;
    width: 100%;
  }

  .team {
    flex: 1;
  }
</style>
