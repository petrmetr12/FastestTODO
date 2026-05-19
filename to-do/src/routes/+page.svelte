<script lang="ts">
    /**let ti
     * {
     *  "text": "Vynést koš",
     *  "completed": false/true
     * }
     */

    let todos = $state<string[]>([]);
    let doneTasks = $state<string[]>([]);
    let newTodo = $state('');

    function addTodo() {
        if (newTodo.trim() !== '') {
            todos.push(newTodo);
            newTodo = '';
        } 
    }
</script>
 
<div class="max-w-100 p-5 border border-gray-400 rounded-4xl bg-gray-500 mx-auto my-12">
    <h1><strong>To-Do List</strong></h1>
    <input type="text" bind:value={newTodo} placeholder="Add a new task" />
    <button onclick={addTodo} class="button">Add</button>
    <button onclick={() => { todos = []; doneTasks = []; }} class="button-each bg-red-300!">Clear All</button>

    <ul>
        {#each todos as todo}
            <li>
                <input 
                    type="checkbox" 
                    value={todo} 
                    bind:group={doneTasks} 
                />
                <span style={doneTasks.includes(todo) ? 'text-decoration: line-through;' : ''}>
                    {todo}
                </span>
                <button onclick={() => {
                    todos = todos.filter(t => t !== todo);
                    doneTasks = doneTasks.filter(t => t !== todo);
                }} class="button-each">Delete</button>
            </li>
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
    button:hover {        
        background-color: #0056b3;
    }
    .container {
        max-width: 400px;
        margin: 50px auto;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 35px;
        background-color: #a0a1a1;
    }
    li {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-bottom: 10px;
    }
</style>