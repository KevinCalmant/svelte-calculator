<script lang="ts">
  export let operation: string;
  export let label: string;
</script>

{#if isNaN(+operation)}
  <div class="button operator" on:click>
    <span class={'icon-' + label}></span>
  </div>
{:else}
  <div class="button number" on:click>
    <span>{label}</span>
  </div>
{/if}

<style type="text/scss" scoped>
.button {
  width: 10em;

  cursor: pointer;
  border: 0.02em solid darkblue;

  height: 2em;
  flex: 1;

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 3em;
  font-weight: bold;
}

.clear {
  font-weight: normal;
}

.operator {
  background-color: darkcyan;
  color: white;
}
</style>