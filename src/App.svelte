<script>
  // import { onDestroy } from "svelte";
  import Button from "./Button.svelte";
  import Resetter from "./Resetter.svelte";
  import { storeCount } from "./store";

  // const unsubscribe = storeCount.subscribe((val) => {
  //   console.log(val);
  // });

  const storeIncreament = () => {
    // storeCount.update((p) => p + 1);
    $storeCount += 1;
  };

  // onDestroy(() => unsubscribe());

  export let name;
  let count;
</script>

<main>
  <div flex>
    <div class="divider">
      <h1>Hello {name}! {count}X 👋</h1>

      <form on:submit={(e) => e.preventDefault()}>
        <input type="text" bind:value={name} />
      </form>

      <Button bind:count label={"Two way bind"} />
      <Button {count} label={"One way bind"} />
      <Button count={0} />
    </div>

    <div class="divider">
      <h1>Store: {$storeCount} {$storeCount ? "🗳" : "🗃"}</h1>
      <Button count={$storeCount} increment={storeIncreament} />
      <Resetter />
    </div>
  </div>
  <br />

  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 440px;
    margin: 0 auto;
  }
  [flex] {
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 1em;
  }
  .divider {
    flex: 1;
    border: 1px solid #ccc;
    padding: 2rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
    [flex] {
      flex-direction: row;
    }
  }
</style>
