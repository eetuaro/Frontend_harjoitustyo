<script>
  //tuodaan modal komponentti tähän komponenttiin
  import Modal from "./modal.svelte";

  let ekanimi = "";
  let tokanimi = "";
  let randomNum = 0;
  let errori = false;
  let näkyvissä = false;

  function randomisoi() {
    //iffissä on validointi että molemmissa input kentissä tulee olla tekstiä ja jos se menee läpi sen jälkeen randomisointi tapahtuu ja modal ikkuna aukeaa.
    if (!ekanimi || !tokanimi) {
      errori = true;
      return;
    }
    randomNum = Math.floor(Math.random() * 100) + 1;
    errori = false;
    näkyvissä = true;
  }
  function tyhjenna() {
    //funktio tyhjentää input kentät sekä sulkee modal ikkunan
    ekanimi = "";
    tokanimi = "";
    randomNum = 0;
    errori = false;
    näkyvissä = false;
  }
</script>

<main>
  <h1>Kiinnostus pronsenttilaskuri</h1>
  <p>
    Laita yksi nimi molempiin kenttiin ja paina kiinnostumisen määrä painiketta
    saadaksesi tietää kuinka kiinnostuneita he ovat toisiinsa.
  </p>
  <input type="text" bind:value={ekanimi} />
  <input type="text" bind:value={tokanimi} />
  <button on:click={randomisoi}>Kiinnostumisen määrä</button>

  <!--jos errori tulee silloin näyttää p elementin ruudulla-->
  {#if errori}
    <p class="error">Syötä molemmat nimet ennen laskennan suorittamista.</p>
  {/if}

  <!--modal komponenttiin välitetyt propsit-->
  <Modal {näkyvissä} {ekanimi} {tokanimi} {randomNum} {tyhjenna} />
</main>

<style>
  main {
    max-width: 400px;
    margin: 0 auto;
    text-align: center;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  h1 {
    font-size: 24px;
    margin-bottom: 10px;
  }

  p {
    font-size: 16px;
    margin-bottom: 20px;
  }

  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  button {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }
  .error {
    color: red;
  }
</style>
