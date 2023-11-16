<template>
  <div class="app flex flex-row justify-center text-center">
    <apexchart
    class="md:w-full md:h-full"
      type="radar"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<script>
import VueApexCharts from "vue3-apexcharts";

export default {
  components: {
    apexchart: VueApexCharts,
  },
  setup() {
    const chartOptions = {
      responsive: [
        {
          breakpoint: 480,
          options: {
            chart: {
              width: 200,
            },
          },
        },
      ],

      chart: {
        type: "radar",
    
      },

      xaxis: {
        categories: [
          "Asociaciones de productores",
          "Empresas Agroindustriales",
          "Agentes Financieros",
          "Empresas Comerciales",
          "Centros de Investigacion",
          "Empresas de Servicio",
          "Personas Naturales",
        ],
      },
    };

    const series = [
      {
        name: "REPRESENTACIÓN ACCIONARIA",
        data: [5.6, 13.5, 3.4, 6.7, 4.5, 13.5, 52.8],
      },
    ];

    return {
      chartOptions,
      series,
    };
  },
};
</script>

  