<script lang="ts">
	import { gsap } from 'gsap/dist/gsap';
	import { onMount } from 'svelte';

	export let side: 'left' | 'right';

	let textScrolling: gsap.core.Tween;

	const el = `.scrolling.${side}`;
	const border = `.border-${side}`;
	const border1 = `.border-1${border}`;
	const border2 = `.border-2${border}`;

	onMount(() => {
		// gsap.registerPlugin(ScrollTrigger);

		// border animation
		gsap.set(border1, {
			y: '-=100%',
			opacity: 1,
		});
		gsap.set(border2, {
			y: '+=100%',
			opacity: 1,
		});
		gsap.to(border1, {
			duration: 0.4,
			y: 0,
		});
		gsap.to(border2, {
			duration: 0.4,
			y: 0,
		});
		// text animation
		gsap.set(el, {
			x: side === 'left' ? '-=500px' : '+=500px',
		});
		gsap.to(el, {
			duration: 0.7,
			x: side === 'left' ? '+=500px' : '-=500px',
			opacity: 1,
			delay: 0.5,
		});
		textScrolling = gsap.to(el, {
			duration: 30,
			y: side === 'left' ? '-=50%' : '+=50%',
			repeat: -1,
			ease: 'none',
			delay: 0.5,
		});
	});

	const speedUp = () => {
		gsap.to(textScrolling, {
			duration: 0.5,
			timeScale: 5,
		});
		gsap.to(border1, {
			duration: 0.3,
			y: '+=100%',
		});
	};
	const slowDown = () => {
		gsap.to(textScrolling, {
			duration: 0.5,
			timeScale: 1,
		});
		gsap.to(border1, {
			duration: 0.3,
			y: 0,
		});
	};
</script>

<div class="container {side}" on:mouseenter={speedUp} on:mouseleave={slowDown} role="presentation">
	{#if side === 'right'}
		<div class="border-{side} border-1 left" />
		<div class="border-{side} border-2 left" />
	{/if}
	<div class="scrolling {side}">
		<slot />
		<!-- duplicate slot to wrap animation -->
		<slot />
	</div>
	{#if side === 'left'}
		<div class="border-{side} border-2 right" />
		<div class="border-{side} border-1 right" />
	{/if}
</div>

<style>
	.container {
		&.left {
			--rotate: 0;
			--writing-mode: vertical-rl;

			padding-left: 5rem;
		}
		&.right {
			--rotate: 180deg;
			--writing-mode: vertical-lr;

			padding-right: 5rem;
		}
	}

	.border-1 {
		display: block;
		height: 100%;
		width: 4px;
		background-color: black;

		&.right {
			margin-left: 6px;
		}
		&.left {
			margin-right: 6px;
		}
	}
	.border-2 {
		display: block;
		height: 100%;
		width: 1px;
		background-color: black;

		&.right {
			margin-left: 1rem;
		}
		&.left {
			margin-right: 1rem;
		}
	}

	.border-left,
	.border-right {
		opacity: 0;
	}

	.scrolling {
		rotate: var(--rotate);
		writing-mode: var(--writing-mode);

		display: flex;
		overflow: hidden;
		position: absolute;
		opacity: 0;

		&.left {
			top: 0;
			left: 4px;
		}
		&.right {
			bottom: 0;
			right: 4px;
		}
	}
	.scrolling :global(> *) {
		font-size: 4rem;
		white-space: nowrap;
		line-height: 5rem;
		cursor: default;
		user-select: none;
	}
</style>
