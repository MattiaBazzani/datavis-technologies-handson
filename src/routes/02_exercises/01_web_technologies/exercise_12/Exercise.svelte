<script>
	let clicked = false;
</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		click here
	</button>
	<!--  -->
</div>

{#if clicked}
	<p><em>You have clicked the button!</em></p>
{:else}
	<p><em>You have to click the button!</em></p>
{/if}
