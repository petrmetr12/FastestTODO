<script lang="ts">
    let todos = $state<{text: string, done: boolean}[]>([]);
    let newTodo = $state('');

    function addTodo() {
        if (newTodo.trim() !== '') {
            todos.push({ text: newTodo.trim(), done: false });
            newTodo = '';
        } 
    }
</script>
 
<div class="max-w-100 p-5 border border-gray-400 rounded-4xl bg-gray-500 mx-auto my-12">
    <h1><strong>To-Do List</strong></h1>
    <input type="text" bind:value={newTodo} placeholder="Add a new task" />
    <button onclick={addTodo} class="bg-yellow-600 hover:bg-yellow-700 focus:outline-1 
                focus:outline-offset-2 focus:outline-yellow-600 active:bg-yellow-800
                pt-2 pb-2">Add</button>
    <button onclick={() => { todos = []; }} class=" bg-red-600 hover:bg-red-700 focus:outline-1 focus:outline-offset-2
                                                     focus:outline-red-600 active:bg-red-800">Clear All
    </button>

    <ul>
        {#each todos as todo}
            <li>
                <input 
                    type="checkbox" 
                    bind:checked={todo.done} 
                />
                <span style={todo.done ? 'text-decoration: line-through;' : ''}>
                    {todo.text}
                </span>
                <button onclick={() => {
                    todos = todos.filter(t => t !== todo);
                }} class="bg-red-600 hover:bg-red-700 focus:outline-1 
                focus:outline-offset-2 focus:outline-red-600 active:bg-red-800
                pt-2 pb-2 br"
        
                >Delete</button>
            </li>
        {/each}
    </ul>
</div>

<style>
    button {
        color: white;
        border: none;
        border-radius: 20px;
        padding: 10px 20px;
        cursor: pointer;
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