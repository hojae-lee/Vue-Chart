<template>
  <canvas ref="LineChart" id="LineChart" width="400" height="400"></canvas>
</template>

<script>
export default {
  props: {
    propsData: Array
  },
  data() {
    return {
      LineChart: {}
    }
  },
  mounted() {
    // const ctx = document.getElementById('LineChart');
    const ctx = this.$refs.LineChart;
    const T = this;

    this.LineChart = new this.$_Chart(ctx, {
      type: 'line',
      data: {
        labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
        datasets: this.propsData
      },
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        },
        onClick: () => {
          T.$emit('refreshChart');
        }
      }
    });
  }
}
</script>

<style>

</style>