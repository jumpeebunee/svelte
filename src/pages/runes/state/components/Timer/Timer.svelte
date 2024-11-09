<script lang="ts">
  import { onMount } from "svelte";

    class Timer {
        isAvailable = $state(false);

        fetchTime() {
            setTimeout(() => {
                this.isAvailable = true;
            }, 2000)
        }
    }

    const timer = new Timer();

    onMount(() => {
        timer.fetchTime();
    })
</script>

<div>Is timer available {timer.isAvailable}</div>

