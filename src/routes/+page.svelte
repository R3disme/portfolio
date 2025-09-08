<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';
	import { Label } from '$lib/components/ui/label';
	import { Textarea } from '$lib/components/ui/textarea';
	import * as Card from '$lib/components/ui/card';
	import * as Carousel from '$lib/components/ui/carousel/index.js';
	import Github from 'lucide-svelte/icons/github';
	import BookText from 'lucide-svelte/icons/book-text';
	import Mail from 'lucide-svelte/icons/mail';
	import Bot from 'lucide-svelte/icons/bot';
	import Laptop from 'lucide-svelte/icons/laptop';
	import Code from 'lucide-svelte/icons/code';
	import Smartphone from 'lucide-svelte/icons/smartphone';
	import User from 'lucide-svelte/icons/user';
	import Bug from 'lucide-svelte/icons/bug';
	import Send from 'lucide-svelte/icons/send';
	import Icon from '$lib/components/ui/icon.svelte';

	const icon_links = [
		{
			label: 'GitHub',
			url: 'https://github.com/r3disme',
			icon: Github
		},
		{
			label: 'Resume',
			url: '',
			icon: BookText
		},
		{
			label: 'Email',
			url: 'mailto:mats@soma.nu',
			icon: Mail
		}
	];

	const technologies = [
		{
			name: 'HTML',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg'
		},
		{
			name: 'CSS',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg'
		},
		{
			name: 'Python',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg'
		},
		{
			name: 'JavaScript',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg'
		},
		{
			name: 'TypeScript',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg'
		},
		{
			name: 'Node.js',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original.svg'
		},
		{
			name: 'Sveltekit',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/svelte/svelte-original.svg'
		},
		{
			name: 'Git',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg'
		}
	];

	const Projects = [
		{
			name: 'SV-Chat',
			description: 'SV-Chat er en chat platform som jeg lagde sammen med en venn',
			image: 'https://i.ibb.co/F4J4XmBK/logo.png',
			url: 'https://github.com/Redveil-SVchat/SVchat'
		},
		{
			name: 'Placeholder',
			description: 'Placeholder',
			image: 'https://i.ibb.co/xtfLyW2M/placeholder-1024x1024.png',
			url: ''
		},
		
	];
	const services = [
		{
			icon: Code,
			title: 'Nettside Koding',
			description: 'Jeg kan hjelpe med å lage en nettside til deg eller din bedrift.'
		},
		{
			icon: Bug,
			title: 'Bug Hunting & fiksing',
			description: 'Finne og fikse bugs i koden din'
		}
	];
	let formData = {
		name: '',
		email: '',
		subject: '',
		message: ''
	};

	let isSubmitting = false;

	const handleSubmit = async (event: Event) => {
		event.preventDefault();
		isSubmitting = true;

		// send form data to backend via post request
    const url = 'https://formspree.io/f/mldwaagb';
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(formData)
    });
		isSubmitting = false;
		// Reset form after submission
		formData = { name: '', email: '', subject: '', message: '' };
	};
</script>

<section class="flex min-h-screen flex-col" id="home">
	<div class="flex flex-1 items-center justify-center px-4 md:px-6">
		<div class="grid gap-6 lg:grid-cols-[1fr_400px] lg:gap-12 xl:grid-cols-[1fr_600px]">
			<div class="flex flex-col justify-center space-y-4">
				<img src="https://i.ibb.co/G4Pg6r4H/img.png" alt="test" width="200px" height="200px" style="border-radius: 50%;">
				<div class="space-y-2">
					<h1 class="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none">
						Mats Dale Soma
					</h1>
					<p class="text-xl">Student</p>
					<p class="max-w-[600px] md:text-xl">
						Jeg er en 16 år gammel student ved Gand VGS som driver med koding på fritid.
					</p>
				</div>
				<div class="flex flex-col gap-2 min-[640px]:flex-row">
					<Button href="#projects">Se prosjekt</Button>
					<Button variant="outline" href="#contact">Kontakt</Button>
				</div>
				<div class="flex space-x-4 self-center sm:self-start">
					{#each icon_links as icon_link}
						<a href={icon_link.url}>
							<svelte:component this={icon_link.icon} class="h-6 w-6" />
							<span class="sr-only">{icon_link.label}</span>
						</a>
					{/each}
				</div>
			</div>
			<div class="flex items-center justify-center"></div>
		</div>
	</div>
</section>
<section id="technologies" class="mx-8">
	<Card.Root class="mx-auto w-full">
		<Card.Header>
			<Card.Title class="text-center text-2xl font-bold">Kodespråk jeg kan</Card.Title>
		</Card.Header>
		<Card.Content>
			<ul class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-4">
				{#each technologies as tech}
					<li
						class="flex flex-col items-center gap-y-1 rounded-lg bg-muted/50 p-2 transition-colors hover:bg-muted"
					>
						<Icon src={tech.icon} class="h-6 w-6" />
						<span class="font-semibold">{tech.name}</span>
					</li>
				{/each}
			</ul>
		</Card.Content>
	</Card.Root>
</section>
<br />
<section id="projects" class="">
	<h2 class="text-center text-2xl font-bold">Utvalgte prosjekter</h2>
	<br />
	<Carousel.Root class="mx-auto w-full max-w-72 md:max-w-lg">
		<Carousel.Content>
			{#each Projects as project}
				<Carousel.Item>
					<Card.Root>
						<Card.Header>
							<Card.Title>{project.name}</Card.Title>
						</Card.Header>
						<Card.Content class="aspect-square items-center justify-center p-6">
							<img src={project.image} alt={project.name} class="h-full w-full object-cover" />
							<br />
							<p>{project.description}</p>
						</Card.Content>
						<Card.Footer>
							<Button href={project.url} class="mx-auto">Mer info</Button>
						</Card.Footer>
					</Card.Root>
				</Carousel.Item>
			{/each}
		</Carousel.Content>
		<Carousel.Previous />
		<Carousel.Next />
	</Carousel.Root>
</section>
<section class="py-12" id="services">
	<div class="container mx-auto px-4">
		<h2 class="mb-8 text-center text-3xl font-bold">Mine Tjenester</h2>
		<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
			{#each services as service, index}
				<Card.Root class="transition-all duration-300 hover:shadow-lg">
					<Card.Header>
						<div class="mb-4 flex h-12 w-12 items-center justify-center rounded-full bg-primary">
							<svelte:component this={service.icon} class="h-6 w-6 text-primary-foreground" />
						</div>
						<Card.Title>{service.title}</Card.Title>
					</Card.Header>
					<Card.Content>
						<Card.Description>{service.description}</Card.Description>
					</Card.Content>
				</Card.Root>
			{/each}
		</div>
	</div>
</section>
<section class="py-12" id="contact">
	<div class="container mx-auto max-w-md px-4">
		<Card.Root>
			<Card.Header>
				<Card.Title class="text-center text-2xl font-bold">Kontakt meg</Card.Title>
				<Card.Description class="text-center">
					Fyll ut skjema under for å kontakte meg.
				</Card.Description>
			</Card.Header>
			<form>
				<Card.Content class="space-y-4">
					<div class="space-y-2">
						<Label for="name">Navn</Label>
						<Input id="name" name="name" placeholder="Ditt navn" bind:value={formData.name} required />
					</div>
					<div class="space-y-2">
						<Label for="email">Epost</Label>
						<Input id="email" name="email" type="email" placeholder="Din Epost" bind:value={formData.email} required />
					</div>
					<div class="space-y-2">
						<Label for="subject">Titel</Label>
						<Input id="subject" name="subject" placeholder="Titel" bind:value={formData.subject} required />
					</div>
					<div class="space-y-2">
						<Label for="message">Inhold</Label>
						<Textarea id="message" name="message" placeholder="Inhold" bind:value={formData.message} required />
					</div>
				</Card.Content>
				<Card.Footer>
					<Button class="w-full" type="submit" disabled={isSubmitting} on:click={handleSubmit}>
						{#if isSubmitting}
							"Sender..."
						{:else}
							Send Meldning
							<Send class="ml-2 h-4 w-4" />
						{/if}
					</Button>
				</Card.Footer>
			</form>
		</Card.Root>
	</div>
</section>
<footer class="py-8 text-center w-full border-2">
  <p>&copy; 2025 Mats Dale Soma. All rights reserved.</p>
</footer>