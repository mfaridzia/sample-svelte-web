<script>
	import Fetch from "./Fetch.svelte";
	import Form from "./Form.svelte";

	let searchTerm;
	let url = "https://jsonplaceholder.typicode.com/users";
	function handleSubmit() {
		const { value } = this.elements.search;
		searchTerm = value; 
	}
</script>

<style>
	h1 {
		color: black;
	}
</style>

<Form {handleSubmit} />
<Fetch url={url} searchTerm={searchTerm} let:data>
	<h1>A list of todos</h1>
	<ul>
		{#each data as user}
			<li> <a href={ "https:/"+user.website}> { user.name } </a> </li>
		{/each}
	</ul>
</Fetch>
