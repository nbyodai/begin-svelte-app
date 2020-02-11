<script>
  import { onMount } from 'svelte'
  export let message;
  onMount(async () => {
    let data = await (await fetch('/api')).json()
    message = data.msg
    console.log('MESSAGE: ', message)
  })
</script>

<style>
  h1 {
    color: purple;
  }
  h2 {
    color: orange;
  }
</style>

<h1>{message}</h1>
<h2>Change me now!</h2>
