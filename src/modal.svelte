<script>
  //exportilla viedään muuttujat tähän komponenttiin
  export let näkyvissä = false;
  export let ekanimi = "";
  export let tokanimi = "";
  export let randomNum = 0;
  export let tyhjenna;
</script>

<!--jos modal ikkuna on auki näyttää siellä p elementin sekä tyhjennä nappulan-->
{#if näkyvissä}
  <div class="modal">
    <p>
      {ekanimi} ja {tokanimi} ovat tämän verran kiinnostuneita toisistaan: {randomNum}%
    </p>
    <button on:click={tyhjenna}>Tyhjennä</button>
  </div>
{/if}

<style>
  .modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  }

  .modal button {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    margin-top: 10px;
  }
</style>
