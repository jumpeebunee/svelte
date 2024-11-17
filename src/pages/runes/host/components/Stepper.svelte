<svelte:options customElement="stepper-component"/>

<script lang="ts">
    const onAction = (type: string) => {
        $host().dispatchEvent(new CustomEvent(type));
    }
</script>

<button onclick={() => onAction("increment")}>increment</button>
<button onclick={() => onAction("decrement")}>decrement</button>