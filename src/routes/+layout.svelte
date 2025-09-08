<script lang="ts">
    import "../app.css";
	import { onMount } from "svelte";
    import { ModeWatcher, toggleMode } from "mode-watcher";
    import { Toaster } from "$lib/components/ui/sonner";
	import { Button } from "$lib/components/ui/button";
    import Code2 from "lucide-svelte/icons/code-xml";
    import Sun from "lucide-svelte/icons/sun";
    import Moon from "lucide-svelte/icons/moon";
    import Cpu from "lucide-svelte/icons/cpu";


    let isMobile = false;
  
    onMount(() => {
      const checkMobile = () => {
        isMobile = window.innerWidth < 768;
      };
      checkMobile();
      window.addEventListener('resize', checkMobile);
      return () => window.removeEventListener('resize', checkMobile);
    });

    const navItems = [
        { label: "technologies", href: "#technologies" },
        { label: "projects", href: "#projects" },
        { label: "services", href: "#services" },
    ];
</script>

<ModeWatcher />
<Toaster />
<body class="font-mono">
    <header class="px-4 lg:px-6 h-14 flex items-center">
        <div class="gap-x-3 flex items-center">
            <a class="flex items-center justify-center" href="/">
                <Code2 class="h-6 w-6" />
                <span class="sr-only">Home page</span>
            </a>
            <Button on:click={toggleMode} variant="ghost" size="icon">
                <Sun
                class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
                />
                <Moon
                class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
                />
                <span class="sr-only">Toggle theme</span>
            </Button>
        </div>
        <nav class="ml-auto flex gap-4 sm:gap-6">
            <a class="text-sm font-medium hover:underline underline-offset-4" href="#technologies">
            Teknologier
            </a>
            <a class="text-sm font-medium hover:underline underline-offset-4" href="#projects">
            Prosjekter
            </a>
            <a class="text-sm font-medium hover:underline underline-offset-4" href="#services">
            Tjenester
            </a>
        </nav>
    </header>
    <slot />
</body>