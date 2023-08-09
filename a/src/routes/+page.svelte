<script>
    import {onMount} from "svelte";

    let iframe

    function getCookie(name) {
        let value = "; " + document.cookie
        let parts = value.split("; " + name + "=")
        if (parts.length === 2) return parts.pop().split(";").shift()
    }

    onMount(
        () => {
            document.cookie = 'a=1'
            document.cookie = 'b=2'

            console.log('PARENT LOADED')
            setTimeout(() => {
                iframe.contentWindow.postMessage({
                    event: 'cookies',
                    cookies: {
                        a: getCookie('a'),
                        b: getCookie('b')
                    }
                }, 'http://localhost:5174/')
                console.log('MESSAGE SENT')
            }, 3000)
        })
</script>

<h1>Das ist Seit A</h1>

<iframe src="http://localhost:5174/" bind:this={iframe}>
</iframe>
