<script lang="ts">
	let { todo = $bindable(), func }: { todo: string; func: () => void } = $props();
</script>

<div class="flex gap-2 mb-6">
	<input
		type="text"
		bind:value={todo}
		placeholder="Add a new task..."
		class="flex-1 p-2 border border-gray-300 rounded focus:outline-none focus:border-blue-400"
	/>
	<button
		onclick={func}
		class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 transition-colors"
	>
		Add
	</button>
</div>
