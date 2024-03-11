<script>
    import {todos} from '../stores';
    import {notifications} from "../notifications";

    export let item;

    const delTodo =id=>{
		todos.delete(id);
		return notifications.danger('Eliminado',3000);
	}

	const editTodo= id =>{
        todos.put(id);
        notifications.warning('Editado',3000);
	}
	$: classIcon = valor =>(
		valor? 'ri-restart-fill':'ri-check-fill'
		)
	$: classState = valor =>
		valor? 'succes':'warning';
</script>

<div class="card">
    <p class={item.state?'lineThrough':''}>{item.text}</p>
    <button class="btn {classState(item.state)}" on:click={()=> editTodo(item.id)}>
        <i class={classIcon(item.state)}></i>
    </button>
    <button class="btn danger" on:click={()=> delTodo(item.id)}>
        <i class="ri-delete-bin-5-fill"></i>
    </button>
</div>