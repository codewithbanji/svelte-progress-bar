<svelte:head>
<style lang="scss">
    @import "bootstrap/scss/functions";
    @import "bootstrap/scss/variables";
    @import "bootstrap/scss/mixins";
	@import 'bootstrap/scss/_progress.scss';
	@import 'bootstrap/scss/_buttons.scss';
</style>
</svelte:head>

<script>
	import ProggressBar from './ProgressBar.svelte';
	import ControlButtons from './ControlButtons.svelte';
	let currIndex = 0;
	let loading = false;
	let paused = false;
	const maxIndex = 5;

	$: done = maxIndex == currIndex;

	function nextItem(){
		setTimeout(() => {
			currIndex++;
			if(currIndex == maxIndex || paused){
				paused = false;
				loading = false;
				return;
			}
			nextItem();
		}, 1000)
	}

	function start(){
	   loading = true;
	   nextItem();
    }

    function pause(){
		paused = true;
	}

    function reset(){
        currIndex = 0;
    } 
</script>

<div style="margin: 20px;">
	<ProggressBar progressPercent={currIndex/maxIndex*100} loading={loading}></ProggressBar>
</div>
<ControlButtons on:start={start} on:pause={pause} on:reset={reset} 
disableStart={loading || done} disablePause={!loading} disableReset={currIndex==0 || loading}></ControlButtons>