<script>
	import { onMount } from 'svelte';
	import MenuWrapper from './MenuWrapper.svelte';
	import ConnectorInside from './ConnectorInside.svelte';

	export let inputUrl = 'https://peerpiper.github.io/iframe-wallet-sdk/';
	export let wallet = null;

	let mounted;

	onMount(() => {
		mounted = true;
	});
</script>

{#if mounted}
	<MenuWrapper let:openNav let:hideNav let:saveInputURL {inputUrl} let:inputUrl>
		<ConnectorInside
			bind:wallet
			show={openNav}
			hide={hideNav}
			on:walletReady
			{inputUrl}
			on:inputUrl={saveInputURL}
		/>
	</MenuWrapper>
{/if}
