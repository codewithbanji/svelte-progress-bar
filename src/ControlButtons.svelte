
<script>
	import { createEventDispatcher } from 'svelte';
    import { Button, Row } from "sveltestrap";

    export let disablePause = true;
    export let disableStart = false;
    export let disableReset = true;
    const dispatch = createEventDispatcher();

    function start(){
        dispatch('start');
    }

    function pause(){
        dispatch('pause');
    }

    function reset(){
        dispatch('reset');
    }

</script>



<div style="text-align: center">
    <Button color="primary" on:click={start} disabled={disableStart}>Start</Button>
    <Button color="secondary" on:click={pause} disabled={disablePause}>Pause</Button>
    <Button color="danger" on:click={reset} disabled={disableReset}>Reset</Button>
</div>
