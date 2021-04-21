<script>
  export let count = 3;
  export let label = "default";

  export let increment = () => {
    count += 1;
  };
</script>

<button on:click={increment}>{label} : {count}</button>
