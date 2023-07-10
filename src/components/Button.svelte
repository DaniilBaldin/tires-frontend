<script>
    let message = ''

    export let color
</script>

<button on:click={()=>message+= 'hello! '}
    style="background: {color}; padding:1rem;">
    Say hello!
</button>

<h2 class="par">{message}</h2>

<style>
    .par{
        color: green;
    }
</style>