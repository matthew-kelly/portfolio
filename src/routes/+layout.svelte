<script lang="ts">
	import '../styles/styles.css';
	import Marquee from './Marquee.svelte';
</script>

<div class="body">
	<Marquee side="left">
		<span class="ultrabold italic">Matt Kelly is a web developer.</span>
		<div class="pad" />
		<span>Matt Kelly is a web developer.</span>
		<div class="pad" />
		<span class="sans">Matt Kelly is a web developer.</span>
		<div class="pad" />
	</Marquee>
	<slot />
	<Marquee side="right">
		<span class="sans">Matt Kelly is a web developer.</span>
		<div class="pad" />
		<span class="ultralight italic">Matt Kelly is a web developer.</span>
		<div class="pad" />
		<span class="ultrabold">Matt Kelly is a web developer.</span>
		<div class="pad" />
	</Marquee>
</div>

<style>
	.body {
		height: 100dvh;
		width: 100dvw;
		overflow: hidden;
		background-color: #fbff3c;
		display: flex;
	}

	.pad {
		display: block;
		width: 1.5rem;
		height: 1rem;
		/* background: blue; */
	}
</style>
