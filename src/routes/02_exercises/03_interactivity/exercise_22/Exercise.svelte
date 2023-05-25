<script>
  let count = 0;
</script>

<button type="button" class="btn btn-primary btn-sm" on on:click={() => count++}>
    Cliked {count}
    {count === 1 ? "time" : "times"}
</button>

<button type ="button" class="btn btn-danger" on:click={() => (count = 0)}>
    Reset
</button>