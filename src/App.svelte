<script lang="ts">
	import LoginForm from './components/LoginForm.svelte'
	import 'vanilla-hcaptcha';
	import Hcap from "./components/Hcap.svelte"

	let color: string = 'blue'
	// function to handle what happens when button is pressed
	const toggle = () => {
		color = (color === 'blue') ? 'red' : 'blue';
	}
	//in package.json --no-clear for local, --host instead for website
</script>

<main>
	<head>
		<meta charset="UTF-8">
		<title>hCaptcha Test</title>
		<script src="https://js.hcaptcha.com/1/api.js" async defer></script>

	</head>
	<h1 style="color: {color}">Login Test Page</h1>
	<LoginForm />
	<button on:click={toggle}>Login</button>
	
	<Hcap />


</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>