<template>
  <div class="app flex flex-row justify-center text-white text-center " ref="chartContainer">
 <canvas ref="radarChart"></canvas>
  
</div>
 
</template>

<script>
import Chart from 'chart.js/auto';

export default {
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const ctx = this.$refs.radarChart.getContext('2d');

      const data = {
        labels: [
          "Asociaciones de productores",
          "Empresas Agroindustriales",
          "Agentes Financieros",
          "Empresas Comerciales",
          "Centros de Investigacion",
          "Empresas de Servicio",
          "Personas Naturales",
        ],
        datasets: [{
          label: 'Porcentaje',
          data: [5.6, 13.5, 3.4, 6.7, 4.5, 13.5, 52.8],
          backgroundColor: 'rgba(75, 192, 192, 0.2)',
          borderColor: 'rgba(75, 192, 192, 1)',
          borderWidth: 1
        }]
      };

      const options = {
        scales: {
          r: {
            angleLines: {
              display: true
            },
            suggestedMin: 0,
            suggestedMax: 20
          }
        }
      };

      this.radarChart = new Chart(ctx, {
        type: 'radar',
        data: data,
        options: options
      });
    }
  },
  beforeDestroy() {
    if (this.radarChart) {
      this.radarChart.destroy();
    }
  }
};
</script>
