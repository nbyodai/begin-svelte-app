<svelte:head>
  <meta charset="UTF-8">
  <title>Chibuzor's Beninging</title>
  <script type="text/javascript" src="https://sdk.userbase.com/1/userbase.js"></script>
  <link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css" rel="stylesheet">
</svelte:head>
<script>
  // initialise userbase
  userbase.init({ appId: 'a19d663f-599e-4878-ba3b-c435c3e4b672' })
	
  let username;
  let password;
  let error;
  
  function handleCreateAccount() {
    userbase.signUp({ username, password, rememberMe: 'none' })
    .then((user) => alert('You signed up!'))
    .catch((e) => error = e)
  }

</script>

<div id="auth-view" class="container mx-auto flex flex-col items-center bg-gray-100 h-screen">
	<h1 class="uppercase m-2 font-semibold text-3xl text-blue-300">Create an account</h1>
	<form id="signup-form" class="flex flex-col items-center mt-8 w-1/2 h-screen">
		<input id="signup-username" class="border-dashed border-2 border-blue-200 border-2 rounded-lg w-2/3 mt-4 p-2 focus:outline-none" type="text" required placeholder="Username" bind:value={username}>
		<input id="signup-password" class="border-dashed border-2 border-blue-200 border-2 rounded-lg w-2/3 mt-4 p-2 focus:outline-none" type="password" required placeholder="Password" bind:value={password}>
		<button class="bg-blue-200 hover:bg-blue-300 text-white font-bold py-2 px-4 border border-blue-300 rounded my-4 w-2/3" on:click={handleCreateAccount}> Create an account</button>
	</form>
	{#if error}
	<div id="signup-error">{error}</div>
	{/if}
</div>
