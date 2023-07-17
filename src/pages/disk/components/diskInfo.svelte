<script>    
    import {onMount} from 'svelte'
    import axios from 'axios'
    const endpoint = import.meta.env.PUBLIC_BASE_URL
    export let Id

    let disk = []

    onMount(async function (){
        const response = await axios.get(`${endpoint}rims/rim?id=${Id}`)
        console.log(response)
        const data = response.data
        console.log(data)
        disk = data
    })
</script>

<section>
    <div>
        <p>{disk.brandName}</p>
    </div>
</section>

<style>

</style>