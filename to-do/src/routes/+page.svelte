<script>
    let todos=$state([]);
    let newTodo = $state('');
    function addTodo() {
        if (newTodo.trim() !== '') {
            todos.push(newTodo.trim());
            newTodo = '';
        }
    }
</script>


<div class="container" >
    <h1><strong>To-Do List</strong></h1>
    <input type="text" bind:value={newTodo} placeholder="Add a new task" />
    <button on:click={addTodo} class="button">Add</button>
    <ul>
        {#each todos as todo}
            <li>{todo}</li>
        {/each}
        
    </ul>
</div>

<style>
    button {
        background-color: #007BFF;
        color: white;
        border: none;
        border-radius: 20px;
        padding: 10px 20px;
        cursor: pointer;
    }
    button:hover {        background-color: #0056b3;
    }
    .container {
        max-width: 400px;
        margin: 50px auto;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 35px;
        background-color: #a0a1a1;
    }
</style>