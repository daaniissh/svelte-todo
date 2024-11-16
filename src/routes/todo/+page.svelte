<script  lang="ts">
	import type { Todo } from '../../types/type';
	import TodoForm from '../../lib/components/TodoForm.svelte';
	import TodoHeader from '../../lib/components/TodoHeader.svelte';
	import TodoList from '../../lib/components/TodoList.svelte';

	
	let list: Todo[] = $state([]);
	let todo = $state('');

	function handleAdd() {
		if (todo !== '') {
			let li = {
				id: Date.now(),
				todo,
				is_checked: false
			};
			list = [...list, li];
			todo = '';
		}
	}
	function handleDelete(id:number) {
     list = list.filter((item)=>item.id != id)
	}
	$inspect(list);
</script>

<div class="min-h-screen bg-gray-100 flex items-center justify-center">
	<div class="w-full max-w-lg p-6 bg-white rounded-lg shadow-lg">
		<TodoHeader />
		<TodoForm bind:todo func={handleAdd} />
		<TodoList {handleDelete} {list} />
	</div>
</div>
