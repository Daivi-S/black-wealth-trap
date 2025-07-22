<script>
  export let title;
  export let text;
</script>

<div class="article-text">
  <h2>{title}</h2>
  <p>{text}</p>
</div>

<style>
  .article-text {
    margin: 50vh auto;
    width: 50%;
    background-color: #ff99fc;
    color: #007052;
    border: solid #8427c9 3px;
    border-radius: 20px;
    padding: 20px;
    box-shadow: 16px 16px #8aa6df;
    text-align: left;
  }

  h2 {
    margin-bottom: 1rem;
    font-size: 1.75rem;
  }
</style>