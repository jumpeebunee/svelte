<script lang="ts">
  import Input from "./components/Input.svelte";

    let message = $state("");
</script>

<p>Message: {message}</p>
<Input bind:message/>