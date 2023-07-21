<script lang='ts'>
	import { AppShell } from '@skeletonlabs/skeleton';
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
	<svelte:fragment slot="header">
		<div class="text-center bg-tertiary-400 h-12 flex items-center justify-center">
			<h1 style="color: red; font-size: 22px"> Top Beast Remodeling Inc. </h1>
		</div>
	</svelte:fragment>

	<svelte:fragment slot="pageHeader">Page Header</svelte:fragment>

	<slot />

	<svelte:fragment slot="footer">
		<div class="text-center">
			<h1> Footer </h1>
		</div>
	</svelte:fragment>
</AppShell>
