<script lang="ts">
    let {message = $bindable()} = $props();
</script>

<input bind:value={message}/>