<template>
  <div>
    <canvas id="myChart"></canvas>
  </div>
</template>

<script>
  import { Chart, registerables } from 'chart.js'

  export default {
    name: "Graph",
    props: ['items'],
    mounted() {
      var ctx = document.getElementById('myChart');

      const dataGraph = {
        labels: this.items.map(item => item['date']),
        datasets: [
          {
            data: this.items.map(item => item['value']),
            backgroundColor: '#698ED1'
          }
        ]
      };

      const optionsGraph = {
        maintainAspectRatio: false,
        animation: {
          duration: 0
        },
        legend: {
          display: false,
        },
        scales: {
          x: {
            grid: {
              color: '#000'
            }
          },
          y: {
            ticks: {
              display: false
            },
            grid: {
              color: function(context) {
                return '#000';
              }
            }
          }
        },
      };

      Chart.register(...registerables);

      const myChart = new Chart(ctx, {
        type: 'bar',
        data: dataGraph,
        options: optionsGraph
      });
    }
  }
</script>

<style scoped>

</style>
