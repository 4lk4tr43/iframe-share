<script>
    import {onMount} from "svelte";

    onMount(() => {
        window.addEventListener('message', ({data}) => {
            console.log('TEST', data)
            for (const cookie in data.cookies) {
                document.cookie = `${cookie}=${data.cookies[cookie]}`
            }
        })
        console.log('IFRAME LOADED')
    })
</script>

<h1>Das ist Seite B (cross domain)</h1>
