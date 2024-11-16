<script lang="ts">
	import type { Todo } from "../../types/type";


	let { list, handleDelete }: { list: Todo[]; handleDelete: (params: number) => void } = $props();
	$inspect(list);
</script>

<ul class="space-y-4 overflow-y-scroll max-h-80">
	{#each list as item (item.id)}
		<li class="flex justify-between items-center p-4 bg-gray-50 rounded shadow">
			<div class="flex items-center gap-2">
				<input bind:checked={item.is_checked} type="checkbox" class="cursor-pointer" />
				<span class="text-gray-700">{item.todo}</span>
			</div>
			<button
				onclick={() => handleDelete(item.id)}
				class="text-red-500 hover:text-red-700 transition-colors"
			>
				Delete
			</button>
		</li>
	{/each}
</ul>
