<script lang="ts">
  import Todos from "./components/Todos.svelte";

    let count = $state(0);
</script>

<div>{count}</div>
<button onclick={() => count++}>Count</button>

<div class="todos">
    <Todos/>
</div>

<style>
    .todos {
        margin-top: 2rem;
    }
</style>