<script>
    import { todos } from "../stores";
    import {notifications} from "../notifications";

    let todo = { id: "", text: "", state: false };

    const addTodo = () => {
        if (!todo.text.trim()) {
            //console.log("vacio");
            todo.text = "";
            return;
        }
        todo.id = Date.now();
        todos.add(todo);
        todo = { id: "", text: "", state: false };

        notifications.success('Agregado',3000);
        
    };
</script>

<form on:submit|preventDefault={addTodo}>
    <input
        type="text"
        placeholder="Enter to add"
        class="formcontrol"
        bind:value={todo.text}
    />
</form>
