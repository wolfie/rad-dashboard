<template>
  <div class="graph">
    <div class="timeline">
      <div class="progress above" :style="{ width: percentager(todayFraction) }"></div>
      <div class="maybe above" :style="{ right: percentager(1-maybeFraction) }">maybe</div>
      <div class="probably above" :style="{ right: percentager(1-probablyFraction) }">probably</div>
      <div class="start underneath">{{ start | dateformatter }}</div>
      <div class="target underneath" :style="{ right: percentager(1-targetFraction) }">{{ target | dateformatter }} ^</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'dash-progress-graph',
    props: {
      start: { type: Date, required: true },
      target: { type: Date, required: true },
      maybe: { type: Date, required: true },
      probably: { type: Date, required: true }
    },
    computed: {
      startTime: function() {
        return this.start.getTime();
      },
      maxTime: function () {
        return (this.target > this.probably) ? this.target.getTime() : this.probably.getTime();
      },
      maxTimeRelative: function () {
        return this.maxTime - this.startTime;
      },
      todayFraction: function () {
        return this.fractionize(new Date());
      },
      maybeFraction: function () {
        return this.fractionize(this.maybe);
      },
      probablyFraction: function () {
        return this.fractionize(this.probably);
      },
      targetFraction: function () {
        return this.fractionize(this.target);
      }
    },
    filters: {
      /** @param {Date} date */
      dateformatter: function(date) {
        return `${date.getUTCFullYear()}-${date.getUTCMonth() + 1}-${date.getUTCDate()}`
      }
    },
    methods: {
      /** @param {number} number */
      percentager: function(number) {
        return (number * 100) + '%';
      },
      /** @param {Date} date */
      fractionize: function(date) {
        return (date.getTime() - this.startTime) / this.maxTimeRelative;
      }
    }
  }
</script>

<style scoped>
  .graph {
    width: 100%;
    position: relative;
    box-sizing: border-box;
  }

  .timeline {
    border-left: 2px solid black;
    border-bottom: 2px solid black;
    box-sizing: border-box;
    height: 20px;
  }

  .progress {
    background-color: #ddd;
    height: 20px;
  }

  .start {
    left: -20px;
  }

  .underneath, .above {
    position: absolute;
  }

  .underneath {
    top: 20px;
  }

  .above {
    top: 0;
  }

  .start {
    position: absolute;
  }

  .maybe, .probably {
    border-right: 2px solid black;
  }
</style>
