<script lang='ts'>
	import { AppShell, AppBar, Drawer, drawerStore } from '@skeletonlabs/skeleton';
	import '@skeletonlabs/skeleton/themes/theme-crimson.css';
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	import '../app.postcss';
	import { onMount } from 'svelte';
	import Navigation from '$lib/components/Navigation.svelte';


	let isMobile = false;
  
	onMount(() => {
	  const mediaQuery = window.matchMedia('(max-width: 768px)'); // Adjust the maximum width as needed
	  isMobile = mediaQuery.matches;
  
	  const updateIsMobile = (event: { matches: boolean; }) => {
		isMobile = event.matches;
	  };
  
	  mediaQuery.addListener(updateIsMobile);
  
	  return () => {
		mediaQuery.removeListener(updateIsMobile);
	  };
	});

	async function openDrawer() {
		drawerStore.open();
	}
	
</script>

<Drawer>
	<Navigation />
</Drawer>




<AppShell>

	<svelte:fragment slot='header'>

	<!-- Original AppBar for desktop -->
	{#if !isMobile}
	<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
	<svelte:fragment slot="lead">
		<a href="/" class="card p-4 rounded-full variant-glass-primary font-bold space-x-3">Top Tier Beast Remodeling (logo here)</a>
	</svelte:fragment>
	<div class="font-bold p-1 space-x-3">
		<a href="about" class="card p-4 rounded-full variant-glass-primary">About</a>
		<a href="gallery" class="card p-4 rounded-full variant-glass-primary">Gallery</a>
		<a href="contact" class="card p-4 rounded-full variant-glass-primary">Contact</a>
	</div>
	<svelte:fragment slot="trail">
		<!-- Optional button for non-mobile screens -->
		<button on:click={openDrawer}>
		<span class="">
			<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
			<rect width="100" height="20" />
			<rect y="30" width="100" height="20" />
			<rect y="60" width="100" height="20" />
			</svg>
		</span>
		</button>
	</svelte:fragment>
	</AppBar>
	{/if}

	<!-- AppBar with only burger menu button for mobile screens -->
	{#if isMobile}
	<AppBar slotTrail="place-content-end">
	<svelte:fragment slot="lead">
		<a href="/" class="card p-4 rounded-full variant-glass-primary font-bold space-x-3">Top Tier Beast Remodeling</a>
	</svelte:fragment>
	<svelte:fragment slot="trail">
		<div class="font-bold p-1 space-x-3">
		<button class="md:hidden btn btn-sm mr-4" on:click={openDrawer}>
			<span>
			<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
				<rect width="100" height="20" />
				<rect y="30" width="100" height="20" />
				<rect y="60" width="100" height="20" />
			</svg>
			</span>
		</button>
		</div>
	</svelte:fragment>
	</AppBar>
	{/if}

	  

	</svelte:fragment>


	<slot />

	<svelte:fragment slot="footer">
		
		<div class="logo-cloud grid-cols-1 lg:!grid-cols-1 gap-1">
			<a class="logo-item" href="https://www.instagram.com/toptierbeastremodelinginc/?igshid=MzRlODBiNWFlZA%3D%3D" target="_blank">
				<span class="h-16 w-16 y">
					<img src="https://cdn-icons-png.flaticon.com/512/1384/1384031.png" alt="Instagram Icon">
				</span>
				<span>Instagram</span>
			</a>
			<!-- <a class="logo-item" href="/">
				<span>(Other Icon)</span>
				<span>Other Title</span>
			</a> -->
			<!-- ... -->
		</div>

	</svelte:fragment>

	
</AppShell>
