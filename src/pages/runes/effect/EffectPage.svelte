<script lang="ts">
    let count = $state(0);
    let ms = $state(1000);
    let div: HTMLDivElement | undefined = undefined;

    let hasScroll = $state(true);

    const seconds = $derived(() => {
        console.log(`update in seconds: ${$effect.tracking()}`)

        return Math.floor(ms / 1000);
    })

    const updateScrollState = () => {
        console.log(`update in scroll: ${$effect.tracking()}`)
        hasScroll = !hasScroll;
    }

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

        if (!div || !hasScroll) return;

        window.scrollTo(0, div.scrollHeight);
    })

    $effect.root(() => {
        $effect(() => {
            count
        })

        $effect(() => {
            ms
        })

        return () => {
            console.log('clean')
        }
    })
</script>

<h1>{count}</h1>
<p>Per {seconds()} seconds, has scroll {hasScroll}</p>
<button onclick={() => (ms *= 2)}>slower</button>
<button onclick={() => (ms /= 2)}>faster</button>

<button onclick={updateScrollState}>update scroll state</button>

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