<script lang="ts">
  let count = $state(0);
</script>

{count}

<stepper-component onincrement={() => count++} ondecrement={() => count--}></stepper-component>