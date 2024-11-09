<script lang="ts">
  import Timer from "./components/Timer/Timer.svelte";
import Todos from "./components/Todos.svelte";

    let count = $state(0);
</script>

<div>{count}</div>
<button onclick={() => count++}>Count</button>

<div class="content">
    <div>
        <Todos/>
    </div>

    <Timer />
</div>

<style>
    .content {
        display: flex;
        align-items: flex-start;
        flex-direction: column;
        margin-top: 2rem;
        gap: 1rem;
    }
</style>