<script>
	// index.svelte has to be as self-contained as possible
	// so users can easily remove it

	import Typewriter from 'svelte-typewriter';
	import Config from '$lib/SveltePress/sveltePress.config';

	import { Button, Tile, Grid, Row, Column } from 'carbon-components-svelte';
	import ArrowRight32 from 'carbon-icons-svelte/lib/ArrowRight32';
	import ArrowDown32 from 'carbon-icons-svelte/lib/ArrowDown32';

	import { session } from '$app/stores';

	$: nav = Config.nav.overwrite
		? Config.nav.items || []
		: $session.get('navbar').concat(Config.nav.items || []);

	let currentYear = new Date().getFullYear();

	// Might be used for more in the future
	const breakpoints = {
		sm: 8
	};

	// Typewriter
	let skills = ['HTML', 'CSS', 'JavaScript'];

	// Logo animation
	import { draw } from 'svelte/transition';

	let duration = 4000;
	let delay = 200;
	let condition = false;
	let finished = false;

	setTimeout(() => (condition = true));
	setTimeout(() => {
		finished = true;
	}, duration - 200); // Fill colors a bit earlier
</script>

<svelte:head>
	<meta name="og:title" content={Config.title} />
	<title>{Config.title}</title>
</svelte:head>

<div class="main">
	<div class="sp--header">
		<Grid padding class="sp--grid">
			<Row>
				<Column style="text-align: center;">
					<svg 
					version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 209.281 209.281" 
					style="margin: 1rem 0; width: 5rem; max-width: 5rem; enable-background:new 0 0 209.281 209.281;" xml:space="preserve">
						<path 
						style="fill: #ff3e00"
						d="M203.456,139.065c3.768-10.786,5.824-22.369,5.824-34.425s-2.056-23.639-5.824-34.425c-0.092-0.324-0.201-0.64-0.333-0.944  C188.589,28.926,149.932,0,104.641,0S20.692,28.926,6.159,69.271c-0.132,0.305-0.242,0.62-0.333,0.944  c-3.768,10.786-5.824,22.369-5.824,34.425s2.056,23.639,5.824,34.425c0.092,0.324,0.201,0.64,0.333,0.944  c14.534,40.346,53.191,69.271,98.482,69.271s83.948-28.926,98.482-69.271C203.255,139.705,203.364,139.39,203.456,139.065z   M104.641,194.281c-3.985,0-10.41-7.212-15.78-23.324c-2.592-7.775-4.667-16.713-6.179-26.436H126.6  c-1.512,9.723-3.587,18.66-6.178,26.436C115.051,187.069,108.626,194.281,104.641,194.281z M80.862,129.521  c-0.721-7.998-1.102-16.342-1.102-24.881s0.381-16.883,1.102-24.881h47.557c0.721,7.998,1.102,16.342,1.102,24.881  s-0.381,16.883-1.102,24.881H80.862z M15.001,104.641c0-8.63,1.229-16.978,3.516-24.881h47.3  c-0.701,8.163-1.057,16.529-1.057,24.881s0.355,16.718,1.057,24.881h-47.3C16.23,121.618,15.001,113.271,15.001,104.641z   M104.641,15c3.985,0,10.411,7.212,15.781,23.324c2.591,7.775,4.667,16.713,6.178,26.435H82.681  c1.512-9.723,3.587-18.66,6.179-26.435C94.231,22.212,100.656,15,104.641,15z M143.464,79.76h47.3  c2.287,7.903,3.516,16.251,3.516,24.881s-1.229,16.978-3.516,24.881h-47.3c0.701-8.163,1.057-16.529,1.057-24.881  S144.165,87.923,143.464,79.76z M184.903,64.76h-43.16c-2.668-18.397-7.245-34.902-13.666-46.644  C152.972,24.865,173.597,42.096,184.903,64.76z M81.204,18.115C74.783,29.857,70.206,46.362,67.538,64.76h-43.16  C35.685,42.096,56.309,24.865,81.204,18.115z M24.378,144.521h43.16c2.668,18.397,7.245,34.902,13.666,46.645  C56.309,184.416,35.685,167.186,24.378,144.521z M128.077,191.166c6.421-11.742,10.998-28.247,13.666-46.645h43.16  C173.597,167.186,152.972,184.416,128.077,191.166z"/>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						<g>
						</g>
						</svg>
					<!-- <svg
						shape-rendering="auto"
						width="250"
						height="250"
						viewBox="0 0 1000 1000"
						xmlns="http://www.w3.org/2000/svg"
					>
						<defs>
							<filter id="null">
								<feBlend mode="normal" in="SourceGraphic" />
							</filter>
						</defs>
						<g filter="url(#null)">
							{#if condition}
								<path
									class:filled-1={finished}
									in:draw={{ duration, delay }}
									d="M250 250v250h500v250H0v150a100 100 0 00100 100h800a100 100 0 00100-100V250H250z"
									fill="#ffd0bf"
								/><path
									class:filled-2={finished}
									in:draw={{ duration, delay }}
									d="M100 0A100 100 0 000 100v650h750V500H250V250h750V100A100 100 0 00900 0H100z"
									fill="#ff3e00"
								/>
							{/if}
						</g>
					</svg> -->
					<h1 style="margin-top: 1rem">វគ្គសិក្សាបង្កើតគេហទំព័រ</h1>
					<p style="margin-top: 1rem; font-size: 1.5rem">[កំពុង​ដំណើរការ...]</p>
					<h3 style="margin: 1rem 0; font-size: 1rem">
						បង្រៀនជាភាសាខ្មែរ 🇰🇭 | Web dev courses taught in Khmer
					</h3>
					<h2 class="subTitle">
						<Typewriter loop={3000} cursor="#ff3e00">
							{#each skills as skill}
								<span>{skill}</span>
							{/each}
							{' '}
						</Typewriter>
					</h2>
					<Button
						icon={ArrowRight32}
						href={nav.length > 0 ? nav[0].link : $session.get('navbar')[0]?.link}
						style="margin-top: 3rem">
						<span style="font-size: 1.24rem; margin-right: -20px">
							បាប់ផ្តើមរៀន
						</span>
					</Button>
				</Column>
			</Row>
		</Grid>
	</div>
	<footer>
		<p>
			គេហទំព័រវគ្គសិក្សានេះបង្កើតឡើងដោយប្រើប្រាស់ 
			<a 
			class="sp--link"
			href="https://sveltepress.geopjr.dev/">SveltePress</a>
		</p>	

		<span class="pd" /> 2021{currentYear === 2021 ? '' : ' - ' + currentYear} -
		<a class="sp--link" href="https://geopjr.dev/">GeopJr</a>
	</footer>
</div>

<style lang="scss">
	:global(.sp--arrow--down) {
		display: flex;
		justify-content: center;
		align-content: center;
		margin: 3rem 0;
	}

	:global(.sp--header) {
		min-height: 100vh;
		max-height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	:global(.sp--grid) {
		margin-bottom: 1rem !important;
	}

	:global(.sp--tile) {
		height: 100%;
	}

	.pd {
		display: inline-flex;
		width: 18px;
		height: 18px;
		vertical-align: middle;
		text-align: center;
		justify-content: center;
	}

	.pd::after {
		content: '🚫';
		display: block;
		position: absolute;
		font-size: 100%;
	}
	.pd::before {
		content: '\00a9';
		display: block;
		position: absolute;
		font-size: 100%;
	}

	.sp--link {
		color: var(--cds-interactive-01);
		text-decoration: none;
	}
	.main {
		padding-top: 3rem;
	}
	.subTitle {
		flex-direction: column;
		display: flex;
		margin-top: 1rem;
	}

	footer {
		font-weight: bold;
		text-align: center;
		padding: 0 2rem 2rem;
	}

	/* md */
	@media only screen and (min-width: 673px) {
		:global(.sp--grid) {
			margin-bottom: 5rem;
		}

		.subTitle {
			flex-direction: row;
			justify-content: center;
		}
	}
</style>
