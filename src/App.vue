<template>
  <div>
    <div style="margin-bottom: 30px">
    <a href="?type=bar">Bar Chart</a>
    &nbsp;
    <a href="?type=doughnut">Doughnut Chart</a>
  </div>
    <BarChart v-if="type === 'bar'" />
    <template v-if="type === 'doughnut'">
      <DoughnutChart :data="dataDoughnut1" chart-id="doughnut1" />
      <DoughnutChart :data="dataDoughnut2" chart-id="doughnut2" />
    </template>

  </div>
</template>

<script>
import BarChart from '@/containers/BarChart.vue';
import DoughnutChart from '@/containers/DoughnutChart.vue';

 export default {
   name: 'App',
   components: {
     BarChart,
     DoughnutChart
   },
   computed: {
     type: function() {
       let t = 'bar';
       const params = new URLSearchParams(window.location.search);
       if (params.has('type')) {
         t = params.get('type');
       }
       return t;
     }
   },
   data() {
     return {
       dataDoughnut1: {
         labels: [ 'January', 'February', 'March' ],
         datasets: [ { label: 'My Doughnut Chart', data: [40, 20, 12], backgroundColor: [
             'rgba(255, 99, 132, 0.2)',
             'rgba(54, 162, 235, 0.2)',
             'rgba(255, 206, 86, 0.2)',
           ],
           borderColor: [
             'rgba(255, 99, 132, 1)',
             'rgba(54, 162, 235, 1)',
             'rgba(255, 206, 86, 1)',
           ],
           borderWidth: 1 } ]
       },
       dataDoughnut2: {
         labels: [ 'April', 'May', 'June' ],
         datasets: [ { label: 'My Doughnut Chart 2', data: [33, 25, 18], backgroundColor: [
             'rgba(255, 99, 132, 0.2)',
             'rgba(54, 162, 235, 0.2)',
             'rgba(255, 206, 86, 0.2)',
           ],
           borderColor: [
             'rgba(255, 99, 132, 1)',
             'rgba(54, 162, 235, 1)',
             'rgba(255, 206, 86, 1)',
           ],
           borderWidth: 1 } ]
       }
     };
   }
 }
</script>

