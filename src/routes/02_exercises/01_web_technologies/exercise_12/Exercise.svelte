<script>
	let clicked = false;
</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		click here
	</button>
	{#if clicked}
		<em>You have clicked the button!</em>
	{:else}
		<em>You have to click the button!</em>
	{/if}
</div>


