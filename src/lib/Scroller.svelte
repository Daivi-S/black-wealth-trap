<script>
  export let layout = 'right';
</script>

<div class="wrapper {layout}">
  <div class="sticky">
    <slot name="sticky" />
  </div>
  <div class="scrolly">
    <slot name="scrolly" />
  </div>
</div>

<style>
  .wrapper {
    background-color: #f7f5eb;
    padding: min(100vh, 30rem) 1rem;
    border-style: solid;
    border-color: #4096fa;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
  }

  .left .scrolly {
    order: 0;
  }
  .left .sticky {
    order: 1;
  }

  .right .scrolly {
    order: 1;
  }
  .right .sticky {
    order: 0;
  }

  .sticky,
  .scrolly {
    display: flex;
    flex-direction: column;
    flex: 1 1;
  }

  .sticky {
    position: sticky;
    top: 50vh;
    transform: translateY(-50%);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 0;
  }

  .scrolly {
    z-index: 1;
  }

  @media (max-width: 768px) {
    .wrapper {
      flex-direction: column;
      padding: 2rem 1rem;
      width: 100vw;
    }

    .sticky,
    .scrolly {
      flex: 1 1 auto;
      min-width: 100%;
      position: static;
      transform: none;
    }

    .sticky {
      margin-bottom: 2rem;
    }
  }
</style>