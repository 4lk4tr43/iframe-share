<script>
    import {onMount} from "svelte";

    onMount(() => {
        window.addEventListener('message', () => console.log('TEST'))
        console.log('IFRAME LOADED')
    })
</script>

<h1>Das ist Seit C</h1>
