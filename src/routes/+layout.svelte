<script lang="ts">
	import '../styles/styles.postcss';
	import Marquee from './Marquee.svelte';

	let marqueeLeft = true;
	let marqueeRight = true;
</script>

<div class="body">
	{#if marqueeLeft}
		<Marquee side="left">
			<span class="ultrabold italic">Matt Kelly is a web developer.</span>
			<div class="pad" />
			<span>Matt Kelly is a web developer.</span>
			<div class="pad" />
			<span class="sans">Matt Kelly is a web developer.</span>
			<div class="pad" />
		</Marquee>
	{/if}

	<div class="content">
		<slot />
	</div>

	{#if marqueeRight}
		<Marquee side="right">
			<span class="sans">Matt Kelly is a web developer.</span>
			<div class="pad" />
			<span class="ultralight italic">Matt Kelly is a web developer.</span>
			<div class="pad" />
			<span class="ultrabold">Matt Kelly is a web developer.</span>
			<div class="pad" />
		</Marquee>
	{/if}
</div>

<style lang="postcss">
	.body {
		min-height: 100dvh;
		width: 100dvw;
		overflow: hidden;
		background-color: #fbff3c;
		display: flex;
		position: relative;
	}

	.content {
		margin: 0;
		display: flex;
		position: relative;
		width: 100%;
	}

	.pad {
		display: block;
		width: 1.5rem;
		height: 1rem;
	}
</style>
