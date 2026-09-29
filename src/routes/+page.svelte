<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import * as Card from '$lib/components/ui/card/index.js';
	import * as Dialog from '$lib/components/ui/dialog/index.js';

	import MenuIcon from '@lucide/svelte/icons/menu';
	import ScrollTextIcon from '@lucide/svelte/icons/scroll-text';
	import XIcon from '@lucide/svelte/icons/x';

	import icon from '$lib/assets/favicon.svg';
	import fabioPassos from '$lib/assets/fabio_passos.jpg';

	let menuOpen = $state(false);
	const closeMenu = () => (menuOpen = false);
</script>

<div class="grid min-h-screen grid-rows-[auto_1fr_auto]">
	<header class="sticky top-0 z-50 border-b-2 border-accent bg-background">
		<div class="mx-auto flex max-w-7xl items-center justify-between px-6 py-4 sm:px-8">
			<div class="flex items-center gap-4">
				<h1 class="text-lg font-semibold sm:text-2xl">AI4HW</h1>
			</div>

			<nav class="hidden items-center gap-8 sm:flex">
				<div class="flex items-center gap-6">
					<a href="#about">About</a>
					<a href="#speakers">Speakers</a>
					<a href="#cfp">Call for Papers</a>
					<a href="#organizers">Organizers</a>
				</div>
				<Button
					class="flex items-center"
					href="https://www.hipeac.net/2027/glasgow/#/"
					target="_blank"
				>
					HiPEAC 2027
				</Button>
			</nav>

			<Button
				variant="ghost"
				size="icon"
				class="sm:hidden"
				aria-label={menuOpen ? 'Close menu' : 'Open menu'}
				aria-expanded={menuOpen}
				onclick={() => (menuOpen = !menuOpen)}
			>
				{#if menuOpen}<XIcon />{:else}<MenuIcon />{/if}
			</Button>
		</div>

		{#if menuOpen}
			<nav
				class="absolute inset-x-0 top-full flex flex-col gap-4 border-b-2 border-accent bg-background px-6 py-6 text-lg sm:hidden"
			>
				<a href="#about" onclick={closeMenu}>About</a>
				<a href="#speakers" onclick={closeMenu}>Speakers</a>
				<a href="#cfp" onclick={closeMenu}>Call for Papers</a>
				<a href="#organizers" onclick={closeMenu}>Organizers</a>
				<Button href="https://www.hipeac.net/2027/glasgow/#/" target="_blank" onclick={closeMenu}>
					HiPEAC 2027
				</Button>
			</nav>
		{/if}
	</header>
	<main class="flex flex-col">
		<div class="border-b border-accent">
			<div class="mx-auto flex max-w-7xl flex-col gap-5 p-8 sm:gap-8 sm:p-24">
				<div class="flex flex-col gap-2">
					<h2 class="max-w-4xl text-3xl font-bold sm:text-6xl">
						Machine Learning Methods and Tools for Hardware Design
					</h2>
					<h3 class="text-lg font-semibold text-accent-foreground sm:text-3xl">
						HiPEAC 2027 Workshop
					</h3>
				</div>
				<div class="flex gap-4">
					<Card.Root class="border border-accent p-4 sm:min-w-48 sm:p-6">
						<Card.Content class="flex flex-col gap-2 p-0">
							<p class="text-md font-bold sm:text-2xl">January 18</p>
							<p class="text-xs text-muted-foreground sm:text-lg">14:00 - 17:00</p>
						</Card.Content>
					</Card.Root>
					<Card.Root class="border border-accent p-4 sm:min-w-48 sm:p-6">
						<Card.Content class="flex flex-col gap-2 p-0">
							<p class="text-md font-bold sm:text-2xl">Etive Room</p>
							<p class="text-xs text-muted-foreground sm:text-lg">Scottish Event Campus</p>
						</Card.Content>
					</Card.Root>
				</div>
			</div>
		</div>
		<div id="about" class="border-b border-accent">
			<div
				class="mx-auto flex max-w-7xl flex-col-reverse items-center justify-between p-8 sm:flex-row sm:gap-4 sm:p-16"
			>
				<img src={icon} alt="AI4HW Logo" class="-mb-6 w-3xs sm:mb-0 sm:w-sm" />
				<div class="flex flex-col gap-4">
					<h3 class="text-left text-xl font-bold sm:text-3xl">
						Unlocking the Potential of AI/ML in Hardware Design
					</h3>
					<p class="text-md max-w-3xl text-justify sm:text-xl">
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
		</div>
		<div id="speakers" class="border-b border-accent">
			<div class="mx-auto flex max-w-7xl flex-col gap-6 p-8 sm:p-16">
				<h3 class="text-xl font-bold sm:text-3xl">Invited Speakers</h3>
				<div class="flex flex-wrap justify-center gap-12 sm:justify-start sm:gap-16">
					<Dialog.Root>
						<Dialog.Trigger>
							<div class="flex flex-col items-start gap-2 hover:cursor-pointer">
								<img
									src={fabioPassos}
									alt="Fábio Passos"
									class="aspect-square w-3xs rounded-2xl object-cover sm:w-xs"
								/>
								<p class="text-2xl font-bold">Fábio Passos</p>
								<div class="flex flex-col items-start gap-0">
									<p class="text-muted-foreground">INESC-ID, Instituto Superior Técnico</p>
									<p class="text-muted-foreground">Celera Semiconductor</p>
								</div>
							</div>
						</Dialog.Trigger>
						<Dialog.Content>
							<Dialog.Header class="px-2 py-6">
								<Dialog.Description class="max-h-[70dvh] scroll-fade overflow-y-auto text-justify">
									Fábio Passos received the Ph.D. degree in Electronic Engineering from the
									University of Seville Seville Spain in 2018. He has held research appointments and
									undertaken research stays at several leading academic and industrial institutions
									including Princeton University, IMEC, Analog Devices, Renesas Electronics,
									SiliconGate and others. He is currently an Assistant Professor with Instituto
									Superior Técnico University of Lisbon Portugal and Vice-Coordinator of the
									Nanoelectronic Circuits and Systems Group at INESC-ID Lisbon Portugal. Dr. Passos
									has received several Best Paper Awards and was the recipient of the 2019
									Outstanding Dissertation Award from the European Design and Automation Association
									(EDAA) recognizing the world's best Ph.D. dissertation in design automation. He is
									an active member of the IEEE Microwave Theory and Technology Society (MTT-S)
									Technical Committee TC-2 on Design Automation and the IEEE Circuits and Systems
									Society (CAS) PECAS Technical Committee. He is the founder and Chair of the
									Portuguese Chapter of the IEEE Council on Electronic Design Automation (CEDA) and
									was elected an IEEE MTT-S Young Professionals Outstanding Lecturer in 2026. His
									research interests include integrated circuit design, AI/ML-assisted design
									methodologies and design automation frameworks for analog and RF circuits.
								</Dialog.Description>
							</Dialog.Header>
						</Dialog.Content>
					</Dialog.Root>

					<Card.Root class="aspect-square min-w-3xs border border-accent sm:mb-22 sm:min-w-xs">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
					<Card.Root class="aspect-square min-w-3xs border border-accent sm:mb-22 sm:min-w-xs">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
				</div>
			</div>
		</div>
		<div id="cfp" class="border-b border-accent">
			<div
				class="mx-auto flex max-w-7xl flex-col-reverse justify-around gap-8 p-8 sm:flex-row sm:items-center sm:gap-4 sm:p-16"
			>
				<ScrollTextIcon size={172} strokeWidth={1} class="self-center text-primary" />
				<div class="flex flex-col gap-4">
					<h3 class="text-left text-xl font-bold sm:text-3xl">Call for Papers</h3>
					<Card.Root class="h-48 min-w-3xs border border-accent sm:min-w-2xl">
						<Card.Content class="text-semibold text-3xl text-accent-foreground">TBA</Card.Content>
					</Card.Root>
				</div>
			</div>
		</div>
		<div id="organizers" class="border-b border-accent">
			<div class="mx-auto flex max-w-7xl flex-col gap-6 p-8 sm:p-16">
				<h3 class="text-xl font-bold sm:text-3xl">Organizers</h3>
				<div
					class="ml-2 flex max-w-2xs flex-col items-center gap-6 sm:ml-0 sm:max-w-none sm:flex-row sm:gap-16"
				>
					<a
						href="https://www.chalmers.se/en/persons/ppedro/"
						target="_blank"
						rel="noopener noreferrer"
						class="flex min-w-3xs flex-1 sm:min-w-xs"
					>
						<Card.Root class="w-full border border-accent p-2 sm:p-4">
							<div>
								<Card.Content class="text-bold text-lg sm:text-xl">Pedro Trancoso</Card.Content>
								<Card.Content class="text-xs text-muted-foreground sm:text-sm"
									>Chalmers University of Technology</Card.Content
								>
							</div>
						</Card.Root>
					</a>
					<a
						href="https://sips.inesc-id.pt/~las/"
						target="_blank"
						rel="noopener noreferrer"
						class="flex min-w-3xs flex-1 sm:min-w-xs"
					>
						<Card.Root class="w-full border border-accent p-2 sm:p-4">
							<div>
								<Card.Content class="text-bold text-lg sm:text-xl">Leonel Sousa</Card.Content>
								<Card.Content class="text-xs text-muted-foreground sm:text-sm"
									>INESC-ID, Instituto Superior Técnico</Card.Content
								>
							</div>
						</Card.Root>
					</a>
					<a
						href="https://www.chalmers.se/en/persons/andcarv/"
						target="_blank"
						rel="noopener noreferrer"
						class="flex min-w-3xs flex-1 sm:min-w-xs"
					>
						<Card.Root class="w-full border border-accent p-2 sm:p-4">
							<div>
								<Card.Content class="text-bold text-lg sm:text-xl">André Carvalho</Card.Content>
								<Card.Content class="text-xs text-muted-foreground sm:text-sm"
									>Chalmers University of Technology</Card.Content
								>
							</div>
						</Card.Root>
					</a>
				</div>
			</div>
		</div>
	</main>
	<footer class="mx-auto flex w-full max-w-7xl items-center justify-end p-6">
		<p class="text-sm text-muted-foreground">© AI4HW - HiPEAC 2027</p>
	</footer>
</div>
