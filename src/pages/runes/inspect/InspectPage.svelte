<script lang="ts">
    let count = $state(0);
    let doubleCount = $derived(count * 2);

    // $inspect(count);
    $inspect(doubleCount).with((t, v) => {
        console.log(v)
    })
</script>

<h1>{count}</h1>
<button onclick={() => count++}>add</button>