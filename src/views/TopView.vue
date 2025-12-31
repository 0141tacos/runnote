<template>
  <div class="graph">
    <div>
      グラフ表示
      <canvas id="time-chart"></canvas>
    </div>
  </div>
  <div class="action">操作ボタン表示領域</div>
</template>
<script setup>
import { onMounted } from 'vue'
import { Chart } from 'chart.js/auto'
import Dammydata from '../dammydata/runnningdata'

onMounted(() => {
  const ctx = document.getElementById('time-chart')
  const dataLabels = Dammydata.map((rows) => rows.date)
  const timeData = Dammydata.map((rows) => rows.pace_sec_per_km)
  console.log(dataLabels)
  new Chart(ctx, {
    type: 'line',
    data: {
      labels: dataLabels,
      datasets: [
        {
          data: timeData,
        },
      ],
    },
  })
})
</script>
