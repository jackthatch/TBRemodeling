<script lang='ts'>
	import { drawerStore } from '@skeletonlabs/skeleton';

    function drawerClose(): void {
        drawerStore.close();

    }
</script>



<nav class='list-nav p-4'>
    <ul>
        <li><a href="/about" on:click={drawerClose}>About Us</a></li>
        <li><a href="/gallery" on:click={drawerClose}>Gallery</a></li>
        <li><a href="/contact" on:click={drawerClose}>Contact</a></li>
    </ul>
</nav>