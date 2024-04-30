<template>
  <div>
    <canvas id="statistik"></canvas>
  </div>
</template>

<script setup>
import Chart from 'chart.js/auto'

const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'Pengunjung',
      data: [30, 40, 50, 40, 20, 50],
      backgroundColor: [
      'rgba(243, 119,	119, 0.99)',
      'rgba(176, 76, 76, 0.50)',
      'rgba(255, 155, 155, 0.90)',
      'rgba(142, 72, 72, 0.90)',
      'rgba(142, 72, 72, 0.90)',
      'rgba(255, 169, 169, 0.90)'
    ],
    }]
  };

  const config = {
    type: 'bar',
    data: data,
    options: {}
  };


onMounted(() => {
  const myChart = new Chart(
    document.getElementById('statistik'),
    config
  );
})
</script>