<script>
  import Scroller from './lib/Scroller.svelte';
  import TitleCard from './lib/TitleCard.svelte';
  import ArticleText from './lib/ArticleText.svelte';
  import BarChart from './lib/BarChart.svelte';

  const steps = [
    {
      id: 1,
      title: 'The Zip Code Wealth Trap',
      text: 'Can your ZIP code decide whether you build wealth? Let’s explore two places — same income, very different futures.',
    },
    {
      id: 2,
      title: 'Same Income',
      text: 'Black households in both ZIP 29840 (SC) and ZIP 60458 (IL) earn around $43,000. On paper, their opportunities look the same.',
    },
    {
      id: 3,
      title: 'Different Wealth',
      text: 'But in 29840, nearly 99% of Black residents own homes. In 60458, that number is just 4.5%.',
    },
    {
      id: 4,
      title: 'Why Place Matters',
      text: 'The difference isn’t income — it’s place. Housing policy. Land access. History. Lending. All shape what income becomes.',
    },
    {
      id: 5,
      title: 'Ask Better Questions',
      text: 'How many other ZIP codes tell this story? Let’s start asking better questions about where wealth can grow.',
    },
  ];
</script>

<main style="min-height: 100vh; background: #f9f9f9; padding: 1rem; border: 2px dashed #ccc;">
  <div style="background-color: #007052; margin: 0; padding: 0;">
    <TitleCard title="The Zip Code Wealth Trap" subtitle="A story of income, race, and place" />
  </div>

  <Scroller layout="right">
    <svelte:fragment slot="sticky">
      <BarChart
        labels={["29840 (SC)", "60458 (IL)"]}
        values={[99, 4.5]} />
    </svelte:fragment>

    <svelte:fragment slot="scrolly">
      {#each steps as step (step.id)}
        <ArticleText title={step.title} text={step.text} />
        {#if step.title === 'Different Wealth'}
          <p style="text-align: center; font-size: 0.85rem; margin-top: 1rem;">
            Explore more ZIP code wealth comparisons at
            <a href="https://blackwealthdata.org/dashboard" target="_blank" style="color: #007052; text-decoration: underline;">
              Black Wealth Data Center
            </a>.
          </p>
          <p style="text-align: center; font-size: 1rem; margin-top: 1rem; font-weight: 500;">
            Wealth isn’t just about earnings — it’s about access, history, and where you’re allowed to plant roots.
          </p>
        {/if}
      {/each}
    </svelte:fragment>
  </Scroller>
</main>
