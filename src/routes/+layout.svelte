<script lang='ts'>
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-crimson.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	// Most of your app wide CSS should be put in this file
	import '../app.postcss';
	import { onMount } from 'svelte';


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
	
</script>


<AppShell>

	<svelte:fragment slot='header'>

	<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
		<svelte:fragment slot="lead">
			<a href="/" class="card p-4 rounded-full variant-glass-primary font-bold space-x-3">Top Tier Beast Remodeling (icon here)</a>
		</svelte:fragment>

		 {#if !isMobile}
			<div class="font-bold p-1 space-x-3">
				<a href="about" class="card p-4 rounded-full variant-glass-primary">About</a>
				<a href="gallery" class="card p-4 rounded-full variant-glass-primary">Gallery</a>
				<a href="contact" class="card p-4 rounded-full variant-glass-primary">Contact</a>
			</div>
		  {/if}
		
		<svelte:fragment slot="trail">
			{#if !isMobile}
				<a href="/" class="card p-4 rounded-full variant-glass-primary font-bold">Optional Button</a>
			{/if}
		</svelte:fragment>
	</AppBar>

	</svelte:fragment>

	

	<!-- <svelte:fragment slot="pageHeader">
		<h1>Header</h1>
	</svelte:fragment> -->

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
