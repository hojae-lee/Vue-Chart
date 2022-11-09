<template>
  <canvas ref="BarChart" id="BarChart" width="400" height="400"></canvas>
</template>

<script>
export default {
  props: {
    propsData: Array
  },
  data() {
    return {
      BarChart: {}
    }
  },
  mounted() {
    // const ctx = document.getElementById('BarChart');
    const ctx = this.$refs.BarChart;
    const T = this;

    this.BarChart = new this.$_Chart(ctx, {
      type: 'bar',
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