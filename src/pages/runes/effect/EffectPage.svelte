<script lang="ts">
    let count = $state(0);
    let ms = $state(1000);
    let div: HTMLDivElement | undefined = undefined;

    $effect(() => {
        const timer = setInterval(() => {
            count += 1;
        }, ms);  

        return () => {
            clearInterval(timer);
        }
    })

    $effect.pre(() => {
        count

        if (!div) return;

        window.scrollTo(0, div.scrollHeight);
    })
</script>

<h1>{count}</h1>
<button onclick={() => (ms *= 2)}>slower</button>
<button onclick={() => (ms /= 2)}>faster</button>

<div bind:this={div} class="items">
    {#each new Array(count) as _, i}
        <div class="item">
            {i}
        </div>
    {/each}
</div>

<style>
    .items {
        display: flex;
        flex-direction: column;
        gap: 16px;
        margin-top: 16px;
    }

    .item {
        width: 400px;
        height: 40px;
        background: #dedcdc;
        border-radius: 8px;
    }
</style>