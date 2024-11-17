<script lang="ts">
    type Props = {
        title: string;
        description?: string;
    }

    let { title, description = "No description" }: Props = $props();
</script>

<h1>{title}</h1>
<p>{description}</p>