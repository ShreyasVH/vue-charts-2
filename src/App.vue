<template>
  <div>
    <div style="margin-bottom: 30px">
    <a href="?type=bar">Bar Chart</a>
    &nbsp;
    <a href="?type=doughnut">Doughnut Chart</a>
  </div>
    <BarChart v-if="type === 'bar'" />
    <DoughnutChart v-if="type === 'doughnut'" />
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
   }
 }
</script>

