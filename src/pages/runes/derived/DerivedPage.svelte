<script lang="ts">
    let count = $state(0);
    let doubled = $derived(count * 2);

    let evenNumber = $derived.by(() => {
        const array = [];

        for (let i = 1; i <= count; i++) {
            if (i % 2 === 0) {
                array.push(i);
            }
        } 

        return array;
    })
</script>

<h2>Counter: {count}, doubled: {doubled}</h2>
<p>Even numbers: {evenNumber}</p>

<button onclick={() => count++}>Count</button>