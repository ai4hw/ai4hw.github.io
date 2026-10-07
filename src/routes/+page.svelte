<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js';
	import * as Card from '$lib/components/ui/card/index.js';
	import * as Dialog from '$lib/components/ui/dialog/index.js';
	import * as Timeline from '$lib/components/ui/timeline/index.js';

	import MenuIcon from '@lucide/svelte/icons/menu';
	import ScrollTextIcon from '@lucide/svelte/icons/scroll-text';
	import XIcon from '@lucide/svelte/icons/x';

	import icon from '$lib/assets/favicon.svg';
	import fabioPassos from '$lib/assets/fabio_passos.jpg';
	import christianPilato from '$lib/assets/christian_pilato.jpg';

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
					<a href="#speakers">Invited Speakers</a>
					<a href="#cfp">Call for Presentations</a>
					<a href="#program">Program</a>
					<a href="#organizers">Organizers</a>
				</div>
				<Button
					class="flex items-center"
					href="https://easychair.org/my/conference?conf=ai4hw2027"
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
				<a href="#speakers" onclick={closeMenu}>Invited Speakers</a>
				<a href="#cfp" onclick={closeMenu}>Call for Presentations</a>
				<a href="#program" onclick={closeMenu}>Program</a>
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
					<h3 class="text-xl font-semibold text-accent-foreground sm:text-3xl">
						HiPEAC 2027 Workshop
					</h3>
				</div>
				<div class="flex gap-4">
					<Card.Root class="shrink-0 border border-accent p-4 sm:min-w-48 sm:px-6 sm:py-4">
						<Card.Content class="flex flex-col gap-1 p-0">
							<p class="text-lg font-bold whitespace-nowrap sm:text-xl">January 18</p>
							<p class="text-sm text-muted-foreground sm:text-base">14:00 - 17:00</p>
						</Card.Content>
					</Card.Root>
					<Card.Root class="border border-accent p-4 sm:min-w-48 sm:px-6 sm:py-4">
						<Card.Content class="flex flex-col gap-1 p-0">
							<p class="text-lg font-bold sm:text-xl">Etive Room</p>
							<p class="text-sm text-muted-foreground sm:text-base">SEC • Glasgow</p>
						</Card.Content>
					</Card.Root>
				</div>
				<Button size="lg" href="#cfp" class="w-fit sm:py-6 sm:text-lg"
					>Call for Presentations</Button
				>
			</div>
		</div>
		<div id="about" class="border-b border-accent">
			<div
				class="mx-auto flex max-w-7xl flex-col-reverse items-center justify-between p-8 sm:flex-row sm:gap-4 sm:p-16"
			>
				<img src={icon} alt="AI4HW Logo" class="-mb-6 w-3xs sm:mb-0 sm:w-sm" />
				<div class="flex flex-col gap-4">
					<h3 class="text-left text-2xl font-bold sm:text-4xl">
						Unlocking the Potential of AI/ML in Hardware Design
					</h3>
					<p class="max-w-3xl text-lg sm:text-justify sm:text-xl">
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
				<h3 class="text-2xl font-bold sm:text-4xl">Invited Speakers</h3>
				<div class="flex flex-wrap items-start justify-center gap-12 sm:justify-start sm:gap-16">
					<Dialog.Root>
						<Dialog.Trigger>
							<div
								id="christian-pilato"
								class="flex flex-col items-start gap-2 hover:cursor-pointer"
							>
								<img
									src={christianPilato}
									alt="Christian Pilato"
									class="aspect-square w-3xs rounded-2xl object-cover sm:w-xs"
								/>
								<p class="text-xl font-bold sm:text-2xl">Christian Pilato</p>
								<div class="flex flex-col items-start gap-0">
									<p class="text-sm text-muted-foreground sm:text-base">Politecnico di Milano</p>
								</div>
							</div>
						</Dialog.Trigger>
						<Dialog.Content>
							<Dialog.Header class="px-4 py-8">
								<Dialog.Description
									class="max-h-[70dvh] scroll-fade overflow-y-auto text-sm sm:text-justify sm:text-base"
								>
									Christian Pilato is an Associate Professor at Politecnico di Milano, where he
									received his Ph.D. in Information Technology in 2011. He was a Postdoctoral
									Researcher at Columbia University and the University of Lugano, and a Visiting
									Researcher at New York University, TU Delft, and Chalmers University of
									Technology. His research focuses on heterogeneous architectures, with emphasis on
									high-level synthesis, memory systems, hardware security, and open-source
									Electronic Design Automation (EDA). He coordinates the Chips JU project ODE4EC-DIG
									on open-source EDA flows for digital chip design, and was Scientific Coordinator
									of the H2020 EVEREST project. He was General Chair of ICCD 2024 and Program Chair
									of several conferences, including ICCD and SAMOS, and is an Associate Editor of
									IEEE TCAD. He is a Senior Member of IEEE and ACM, a Member of HiPEAC and
									DISCOVER-US, and currently Chair of ACM SIGDA.
								</Dialog.Description>
							</Dialog.Header>
						</Dialog.Content>
					</Dialog.Root>
					<Dialog.Root>
						<Dialog.Trigger>
							<div id="fabio-passos" class="flex flex-col items-start gap-2 hover:cursor-pointer">
								<img
									src={fabioPassos}
									alt="Fábio Passos"
									class="aspect-square w-3xs rounded-2xl object-cover sm:w-xs"
								/>
								<p class="text-xl font-bold sm:text-2xl">Fábio Passos</p>
								<div class="flex flex-col items-start gap-0">
									<p class="text-sm text-muted-foreground sm:text-base">
										INESC-ID, Instituto Superior Técnico
									</p>
									<p class="text-sm text-muted-foreground sm:text-base">Celera Semiconductor</p>
								</div>
							</div>
						</Dialog.Trigger>
						<Dialog.Content>
							<Dialog.Header class="px-4 py-8">
								<Dialog.Description
									class="max-h-[70dvh] scroll-fade overflow-y-auto text-sm sm:text-justify sm:text-base"
								>
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
				</div>
			</div>
		</div>
		<div id="cfp" class="border-b border-accent">
			<div
				class="mx-auto flex max-w-7xl flex-col-reverse justify-around gap-8 p-8 sm:flex-row sm:items-center sm:gap-4 sm:p-16"
			>
				<ScrollTextIcon size={164} strokeWidth={1} class="self-center text-primary" />
				<div class="flex max-w-3xl flex-col gap-5">
					<h3 class="text-left text-2xl font-bold sm:text-4xl">Call for Presentations</h3>
					<p class="text-base sm:text-justify sm:text-lg">
						We welcome informal contributions from industry and academia, especially
						<strong>work in progress</strong> and <strong>lessons learned</strong> from applying AI/ML
						in real design flows.
					</p>
					<div class="flex flex-col gap-2">
						<h4 class="text-lg font-semibold sm:text-xl">Topics of interest</h4>
						<ul class="list-disc space-y-1 pl-5 text-base sm:text-lg">
							<li>Performance and efficiency modeling based on AI</li>
							<li>AI-driven architecture design and space exploration (DSE)</li>
							<li>AI for IC and IC for AI</li>
						</ul>
					</div>
					<Card.Root
						class="flex flex-col gap-4 border border-accent p-4 sm:flex-row sm:items-center sm:justify-between sm:px-6 sm:py-4"
					>
						<Card.Content class="flex flex-col p-0">
							<p class="text-lg sm:text-xl">
								Deadline: <span class="font-bold text-accent-foreground">02-11-2026 AoE</span>
							</p>
							<p class="text-sm text-muted-foreground sm:text-base">No formal proceedings.</p>
						</Card.Content>
						<Button
							href="https://easychair.org/conferences/?conf=ai4hw2027"
							target="_blank"
							rel="noopener noreferrer"
							class="w-fit sm:text-lg"
						>
							Submit
						</Button>
					</Card.Root>
					<p class="text-sm text-muted-foreground sm:text-base">
						Accepted contributions include a 5 minute presentation followed by discussion. Submit a
						one-page PDF abstract with the title, presenter name(s), affiliation, and a short
						description of the challenge, insight, or lesson you would like to discuss. No template
						is required. All presenters and participants must register for the HiPEAC conference to
						attend.
					</p>
				</div>
			</div>
		</div>
		<div id="program" class="border-b border-accent">
			<div class="mx-auto flex max-w-7xl flex-col gap-6 p-8 sm:p-16">
				<h3 class="text-2xl font-bold sm:text-4xl">Program</h3>
				<Timeline.Root size="lg">
					<Timeline.Item>
						<Timeline.Indicator></Timeline.Indicator>
						<Timeline.Content class="gap-4">
							<div class="flex flex-col gap-1">
								<p class="text-lg font-semibold sm:text-xl">
									Open Flows, Better Models: Why AI for Hardware Needs Open-Source EDA
								</p>
								<a href="#christian-pilato">
									<p class="text-sm text-muted-foreground sm:text-base">Christian Pilato • TBA</p>
								</a>
							</div>
							<p class="text-base sm:text-justify sm:text-lg">
								Machine learning, including large language models, is increasingly being applied
								across the hardware design flow, from high-level synthesis to physical
								implementation. Building better models requires diverse training data, reliable
								feedback from design tools, and the ability to generalize across designs and
								technologies. This talk argues that open-source EDA provides essential
								infrastructure for meeting these needs. Open tools, designs, and PDKs can support
								systematic generation of datasets spanning multiple abstraction levels and enable
								tool feedback to guide model training and refinement. They also allow researchers to
								explore how tool versions, configurations, and target technologies affect design
								outcomes, helping develop models that remain effective beyond a single experimental
								setup. Reproducible flows provide a common basis for measuring these improvements.
								The talk will discuss open challenges in data quality, scalability, and transfer to
								industrial flows, highlighting the role of European open-source EDA initiatives.
							</p>
						</Timeline.Content>
					</Timeline.Item>
					<Timeline.Item>
						<Timeline.Indicator></Timeline.Indicator>
						<Timeline.Content class="gap-4">
							<div class="flex flex-col gap-1">
								<p class="text-lg font-semibold sm:text-xl">
									AI/ML-Driven Design of RF and mm-Wave Circuits and Systems: Advances and Future
									Trends
								</p>
								<a href="#fabio-passos">
									<p class="text-sm text-muted-foreground sm:text-base">Fábio Passos • TBA</p>
								</a>
							</div>
							<p class="text-base sm:text-justify sm:text-lg">
								The growing complexity of hardware systems for next-generation wireless
								communication, sensing, and satellite applications is challenging traditional design
								methodologies. Artificial intelligence (AI) and machine learning (ML) are emerging
								as key enablers for accelerating hardware development, reducing design effort, and
								improving design efficiency. In particular, RF and millimeter-wave circuits pose
								unique challenges due to their nonlinearities, large design spaces, expensive
								electromagnetic simulations, and sensitivity to process, voltage, and temperature
								variations. This talk reviews recent advances in AI/ML-driven design methodologies
								for RF and mm-Wave circuits and systems, covering device modeling, passive device
								synthesis, electromagnetic-aware optimization, circuit sizing, layout generation,
								and system-level co-design. Using RF and mm-Wave design as a representative case
								study, the talk discusses how AI can be integrated across the hardware design flow
								and highlights emerging trends toward end-to-end and autonomous design environments,
								as well as the key challenges and opportunities ahead.
							</p>
						</Timeline.Content>
					</Timeline.Item>
					<Timeline.Item>
						<Timeline.Indicator></Timeline.Indicator>
						<Timeline.Content class="gap-4">
							<div class="flex flex-col gap-1">
								<p class="text-lg font-semibold sm:text-xl">TBA</p>
							</div>
						</Timeline.Content>
					</Timeline.Item>
				</Timeline.Root>
			</div>
		</div>
		<div id="organizers" class="border-b border-accent">
			<div class="mx-auto flex max-w-7xl flex-col gap-6 p-8 sm:p-16">
				<h3 class="text-2xl font-bold sm:text-4xl">Organizers</h3>
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
								<Card.Content class="text-lg font-bold sm:text-xl">Pedro Trancoso</Card.Content>
								<Card.Content class="text-sm text-muted-foreground sm:text-base"
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
								<Card.Content class="text-lg font-bold sm:text-xl">Leonel Sousa</Card.Content>
								<Card.Content class="text-sm text-muted-foreground sm:text-base"
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
								<Card.Content class="text-lg font-bold sm:text-xl">André Carvalho</Card.Content>
								<Card.Content class="text-sm text-muted-foreground sm:text-base"
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
