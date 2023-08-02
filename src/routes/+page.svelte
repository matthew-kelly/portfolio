<div class="container center">
	<div class="main-banner">
		<div class="banner-center">
			<h1>Matt Kelly</h1>
			<h2>web developer</h2>
		</div>
		<p>*and sourdough baker</p>
	</div>
</div>

<style lang="postcss">
	.container {
		flex-direction: column;
		margin: auto;
		padding: 2rem;
		height: 100%;
		width: 100%;
	}

	.main-banner {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		width: 100%;
		height: 100%;
		text-align: center;
		user-select: none;

		h1 {
			font-size: 13rem;
			font-weight: 400;
			margin-bottom: 2rem;
		}
		h2 {
			font-family: 'PPRightGothic-Wide';
			font-size: 6rem;
			font-weight: 800;
		}
		p {
			position: absolute;
			bottom: 0;
			right: 2rem;
			font-size: 2.5rem;
			font-weight: 200;
			align-self: flex-end;
			margin-bottom: 2rem;
		}
	}

	.banner-center {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
	}
</style>
