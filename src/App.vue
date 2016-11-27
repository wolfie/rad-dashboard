<template>
  <div class="root">
    <div class="row">
      <DashPanel title="Who's on #support?" class="support">
        <DashSupport :supports="supports"></DashSupport>
      </DashPanel>
    </div>
    <div class="row stretch">
      <DashPanel title="What's going on now?" class="now">
        <DashProgress></DashProgress>
      </DashPanel>
      <DashPanel title="What happened recently?" class="recent">
        <DashDone></DashDone>
      </DashPanel>
    </div>
  </div>
</template>

<script>
import DashPanel from './components/DashPanel'
import DashSupport from './components/DashSupport'
import DashProgress from './components/DashProgress'
import DashDone from './components/DashDone'

export default {
  name: 'app',
  components: {
    DashPanel,
    DashSupport,
    DashProgress,
    DashDone
  },
  data: function() { return {
    supports: {
      'Framework': {
        name: 'John Smith',
        info: {
          'Skype': 'jsmith',
          'Flowdock': '#framework-support',
          'Slack': '#framework-support'
        }
      }
    }
  } }
}
</script>

<style>
  .root {
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  .row {
    width: 100%;
    display: flex;
  }

  .row > * {
    width: 100%;
  }

  .row.stretch {
    flex-grow: 1;
  }
</style>
