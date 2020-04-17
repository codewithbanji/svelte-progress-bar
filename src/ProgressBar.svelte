


<style>
	:global(div.progress){
		height: 2rem;
		font-size: 1.5rem;
	}
</style>

<script>
  	import Progress from 'sveltestrap/src/Progress.svelte';

	export let progressPercent = 0;
	export let loading = false;
</script>

<Progress value={progressPercent} animated={loading} striped=true>{progressPercent + "%"}</Progress>
