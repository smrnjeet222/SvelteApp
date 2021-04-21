<script>
  import { storeCount } from "./store";

  const reset = () => ($storeCount = 0);
</script>

<button on:click={reset}>Reset Store</button>
