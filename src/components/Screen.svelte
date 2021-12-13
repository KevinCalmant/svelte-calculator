<script lang="ts">
  export let calculation: string;
  export let result: number;
</script>

<div class="screen">
  <div class="screen-member">
    <h3>{calculation}</h3>
  </div>
  <div class="screen-member">
    <h1>{result}</h1>
  </div>
</div>

<style lang="scss">
.screen {
  height: 6em;
  background-color: slategray;
  padding: 1em;
}

.screen-member {
  height: 3em;
  display: flex;
  justify-content: flex-end;
  align-items: center;

  h1,
  h3 {
    color: white;
  }
}
</style>