<script>
  let count = 0;
  const increment = () => {
    count++;
  };
</script>

<style>
  
</style>

<h2>Counter</h2>
<input type="text" bind:value={count} readonly>
<button on:click={increment}>count</button>
