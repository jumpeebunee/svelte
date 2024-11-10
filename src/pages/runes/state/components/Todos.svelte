<script lang="ts">
    let title = $state('');

    let updated = $state(true);
    let todos = $state.raw([{title: "add more todos", done: false}])

    const addTodo = (text: string) => {
        updated = false;
        todos.push({title: text, done: false});
        title = "";
    }

    const updateArray = () => {
        updated = true;
        todos = [...todos];
    }

    const getSnapshot = () => {
        const x = $state.snapshot(todos);
        console.log(x)
    }
</script>

<input bind:value={title} type="text" placeholder="todo name">

<div class="buttons">
    <button disabled={!title} onclick={() => addTodo(title)}>add</button>
    <button disabled={updated} onclick={updateArray}>update array</button>
    <button onclick={getSnapshot}>get snapshot</button>
</div>

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