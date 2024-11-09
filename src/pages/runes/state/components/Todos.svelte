<script lang="ts">
    let title = $state('');

    const todos = $state([{title: "add more todos", done: false}]);

    const addTodo = (title: string) => {
        todos.push({title, done: false});
        title = "";
    }
</script>

<input bind:value={title} type="text" placeholder="todo name">
<button disabled={!title} onclick={() => addTodo(title)}>add</button>

<div class="todos">
    {#each todos as todo}
        <div class="todo">
            <div class="title">{todo.title}</div>
            <div>done: {todo.done}</div>
        </div>
    {/each}
</div>

<style>
    .todos {
        margin-top: 1rem;
    }

    .todo {
        width: 240px;
        padding: 1rem 1.75rem;
        border: solid 1px black;
    }

    .title {
        font-size: 18px;
    }
</style>