<script>
	import axios from 'axios';

	let username = '';
	let password = '';

	// Featch API
	const url = 'https://authentication.kordis.fr/oauth/authorize?response_type=token&client_id=skolae-app';

	// Async / Await
	const getData = async (url) => {
		try {
			const response = await axios({
				method: 'GET',
				url: 'https://authentication.kordis.fr/oauth/authorize?response_type=token&client_id=skolae-app',
				headers: {
					Authorization: `Basic ${btoa(username + ':' + password)}`,
				},
				maxRedirects: 0,
			});

			console.log('response.data:', response.data);

			const response2 = await axios(response.data.location.url);

			console.log('response2.data:', response2.data);
		} catch (error) {
			console.log(error);
		}
	};

</script>

<main>
	<div class="wrapper flex">
		<h1 class="title flex">Mini-Corner CSV Cleaner</h1>
		<input type="text" bind:value={username}>
		<input type="password" bind:value={password}>
		<button class="button login" on:click={() => getData(url)}>Login</button>
	</div>
</main>

<style>
</style>
