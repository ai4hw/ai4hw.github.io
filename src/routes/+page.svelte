<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import * as Card from '$lib/components/ui/card/index.js';

	import ExternalLinkIcon from '@lucide/svelte/icons/external-link';

	import icon from '$lib/assets/favicon.svg';
</script>

<div class="grid min-h-screen grid-rows-[auto_1fr_auto]">
	<header
		class="sticky top-0 z-50 flex items-center justify-between border-b-2 border-accent bg-background px-8 py-4"
	>
		<div class="flex items-center gap-4">
			<h1 class="text-3xl font-semibold">AI4HW</h1>
		</div>

		<nav class="flex items-center gap-8">
			<div class="flex items-center gap-6">
				<a href="#about">About</a>
				<a href="#speakers">Speakers</a>
			</div>
			<Button
				class="flex items-center"
				href="https://www.hipeac.net/2027/glasgow/#/"
				target="_blank"
			>
				HiPEAC 2027
				<ExternalLinkIcon />
			</Button>
		</nav>
	</header>
	<main class="flex flex-col">
		<div class="flex flex-col justify-center">
			<div class="flex scroll-mt-24 flex-col gap-10 border-b border-accent p-24">
				<div class="flex flex-col gap-2">
					<h2 class="w-4xl text-6xl font-bold">
						Machine Learning Methods and Tools for Hardware Design
					</h2>
					<h3 class="text-3xl font-semibold text-accent-foreground">HiPEAC 2027 Workshop</h3>
				</div>
				<div class="flex gap-4">
					<Card.Root class="min-w-48 border border-accent">
						<Card.Content class="flex flex-col gap-2">
							<p class="text-2xl font-bold">January 18</p>
							<p class="text-lg text-muted-foreground">14:00</p>
						</Card.Content>
					</Card.Root>
					<Card.Root class="min-w-48 border border-accent">
						<Card.Content class="flex flex-col gap-2">
							<p class="text-2xl font-bold">Etive Room</p>
							<p class="text-lg text-muted-foreground">Scottish Event Campus</p>
						</Card.Content>
					</Card.Root>
				</div>
			</div>
			<div id="about" class="flex items-center justify-between gap-4 border-b border-accent p-24">
				<img src={icon} alt="AI4HW Logo" class="w-sm opacity-100" />
				<div class="flex flex-col gap-4">
					<h3 class="text-left text-3xl font-bold">
						Unlocking the Potential of AI/ML in Hardware Design
					</h3>
					<p class="max-w-3xl text-justify text-xl">
						Modern hardware design is outgrowing traditional EDA workflows due to exploding design
						complexity, tighter time-to-market pressure, and nanoscale physical constraints that
						limit classical heuristics. AI/ML offer a promising path forward, already being applied
						across the design flow with notable successes like DeepMind's AlphaChip (RL-based
						floorplanning) and NVIDIA's ChipNeMo (a hardware-focused LLM), yet the field remains
						fragmented due to unresolved issues in generalizability, tool integration, dataset
						availability, and the academic-to-industrial gap—challenges that the AI4HW workshop aims
						to address by uniting AI and hardware researchers to share progress and drive more
						intelligent, automated, scalable design flows.
					</p>
				</div>
			</div>
			<div id="speakers" class="flex scroll-mt-24 flex-col gap-6 border-b border-accent p-24">
				<h3 class="text-3xl font-bold">Speakers</h3>
				<div class="flex gap-12">
					<Card.Root class="aspect-square min-w-xs border border-accent">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
					<Card.Root class="aspect-square min-w-xs border border-accent">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
					<Card.Root class="aspect-square min-w-xs border border-accent">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
				</div>
			</div>
		</div>
	</main>
	<footer class="flex items-center justify-end p-6">
		<p class="text-sm text-muted-foreground">© AI4HW - HiPEAC 2027</p>
	</footer>
</div>
