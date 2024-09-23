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
			url: 'https://github.com/spit-fires',
			icon: Github
		},
		{
			label: 'Resume',
			url: '',
			icon: BookText
		},
		{
			label: 'Email',
			url: '',
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
			name: 'Fastapi',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fastapi/fastapi-original.svg'
		},
		{
			name: 'Sveltekit',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/svelte/svelte-original.svg'
		},
		{
			name: 'MongoDB',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mongodb/mongodb-original.svg'
		},
		{ name: 'Pocketbase', icon: 'https://avatars.githubusercontent.com/u/101000011?s=200&v=4' },
		{
			name: 'Tailwind',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tailwindcss/tailwindcss-original.svg'
		},
		{
			name: 'Git',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg'
		},
		{
			name: 'XML',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/xml/xml-original.svg'
		},
		{
			name: 'SQLite',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/sqlite/sqlite-original.svg'
		},
		{
			name: 'Discord.js',
			icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/discordjs/discordjs-original.svg'
		},
		{ name: 'Pycord', icon: 'https://pycord.dev/_next/static/media/logo.2762350e.png' }
	];

	const Projects = [
		{
			name: 'Openimagery',
			description: 'Fully free API for generating AI images. Supports multiple styles and models.',
			image: 'https://i.postimg.cc/8PzF6B6M/image.png',
			url: 'https://github.com/OpenImagery/docs'
		},
		{
			name: 'Pawnbadges-SCP',
			description: 'A rimworld mod that adds SCP themed badges to the game.',
			image:
				'https://raw.githubusercontent.com/Spit-fires/pawnbadges-scp/refs/heads/main/About/Preview.png',
			url: 'https://github.com/Spit-fires/pawnbadges-scp'
		},
		{
			name: 'Linked',
			description:
				'A web application that allows users to create and share their own social media links in a single page.',
			image: 'https://i.postimg.cc/J0947HDT/image.png',
			url: ''
		}
	];
	const services = [
		{
			icon: Code,
			title: 'Web Development',
			description: 'Creating responsive and performant web applications using modern technologies.'
		},
		{
			icon: Laptop,
			title: 'Desktop App Development',
			description: 'Building desktop applications for Windows, macOS, and Linux.'
		},
		{
			icon: Smartphone,
			title: 'Mobile App Development',
			description: 'Building cross-platform mobile applications for iOS and Android.'
		},
		{
			icon: Bot,
			title: 'Bot Development',
			description: 'Creating Discord bots for your server with custom features.'
		},
		{
			icon: User,
			title: 'Consulting',
			description:
				'Providing consulting services for your projects and helping you make the right decisions.'
		},
		{
			icon: Bug,
			title: 'Bug Hunting & Fixing',
			description: 'Fixing bugs and issues in your applications to make them more stable.'
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
    const url = 'https://formspree.io/f/xgvwjpdr';
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
				<div class="space-y-2">
					<h1 class="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none">
						Fahad Hossain
					</h1>
					<p class="text-xl">Software Engineer</p>
					<p class="max-w-[600px] md:text-xl">
						Passionate about creating efficient, scalable, and user-friendly applications.
						Specializing in full-stack development with expertise in Sveltekit, Python, and cloud
						technologies.
					</p>
				</div>
				<div class="flex flex-col gap-2 min-[640px]:flex-row">
					<Button>View Projects</Button>
					<Button variant="outline">Contact</Button>
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
			<Card.Title class="text-center text-2xl font-bold">Technologies I Know</Card.Title>
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
	<h2 class="text-center text-2xl font-bold">Notable Projects</h2>
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
							<Button href={project.url} class="mx-auto">View Project</Button>
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
		<h2 class="mb-8 text-center text-3xl font-bold">My Services</h2>
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
<section class="py-12">
	<div class="container mx-auto max-w-md px-4">
		<Card.Root>
			<Card.Header>
				<Card.Title class="text-center text-2xl font-bold">Contact Me</Card.Title>
				<Card.Description class="text-center">
					Fill out the form below to get in touch with me.
				</Card.Description>
			</Card.Header>
			<form>
				<Card.Content class="space-y-4">
					<div class="space-y-2">
						<Label for="name">Name</Label>
						<Input id="name" name="name" placeholder="Your name" bind:value={formData.name} required />
					</div>
					<div class="space-y-2">
						<Label for="email">Email</Label>
						<Input id="email" name="email" type="email" placeholder="Your email" bind:value={formData.email} required />
					</div>
					<div class="space-y-2">
						<Label for="subject">Subject</Label>
						<Input id="subject" name="subject" placeholder="Subject" bind:value={formData.subject} required />
					</div>
					<div class="space-y-2">
						<Label for="message">Message</Label>
						<Textarea id="message" name="message" placeholder="Your message" bind:value={formData.message} required />
					</div>
				</Card.Content>
				<Card.Footer>
					<Button class="w-full" type="submit" disabled={isSubmitting} on:click={handleSubmit}>
						{#if isSubmitting}
							"Sending..."
						{:else}
							Send Message
							<Send class="ml-2 h-4 w-4" />
						{/if}
					</Button>
				</Card.Footer>
			</form>
		</Card.Root>
	</div>
</section>
<footer class="py-8 text-center w-full border-2">
  <p>&copy; 2024 Fahad Hossain. All rights reserved.</p>
</footer>