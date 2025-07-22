<script lang="ts">
  import { onMount } from 'svelte';
  import Chart from 'chart.js/auto';

  export let labels: string[] = [];
  export let values: number[] = [];

  let canvas: HTMLCanvasElement;

  onMount(() => {
    const ctx = canvas.getContext('2d');

    new Chart(ctx, {
      type: 'bar',
      data: {
        labels,
        datasets: [
          {
            label: 'Black Homeownership Rate (%)',
            data: values,
            backgroundColor: ['#2a9d8f', '#888'],
            borderRadius: 6
          }
        ]
      },
      options: {
        responsive: true,
        plugins: {
          tooltip: {
            callbacks: {
              label: ctx => `${ctx.dataset.label}: ${ctx.raw}%`
            }
          },
          legend: {
            display: false
          },
          title: {
            display: true,
            text: 'Homeownership Comparison: 29840 vs. 60458',
            font: {
              size: 18
            }
          }
        },
        scales: {
          y: {
            beginAtZero: true,
            max: 100,
            title: {
              display: true,
              text: 'Percent of Black Households Owning Homes'
            }
          }
        }
      }
    });
  });
</script>

<canvas bind:this={canvas} width="400" height="300" style="margin: 2rem auto; display: block;"></canvas>