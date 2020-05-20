<script>
  export let name;
  let data = [];
  import Card from "./Card.svelte";
  let promise = async () => {
    const res = await fetch("assets/data/data.json");
    const response = await res.text().then(data => JSON.parse(data));
    console.log("response ", (data = response));
    return response;
  };
  promise();
</script>

<style>
  div {
    display: flex;
    flex-wrap: wrap;
	justify-content: center;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #000;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>{name}</h1>
  {#await promise}
    <p>...waiting</p>
  {:then response}

    <div class="container">
      {#each data as { character, image }, i}
        <Card name={character} picture={image} />
      {/each}
    </div>
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}

</main>
