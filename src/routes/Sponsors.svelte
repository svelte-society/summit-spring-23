<script lang="ts">
	import { PUBLIC_API_URL } from '$env/static/public';
	import Sponsor from './Sponsor.svelte';

	export let sponsors: Sponsor;
</script>

<article id="sponsors" class="bg-papaya-400 text-black">
	<div class="grid gap-4 w-full sm:w-4/5 md:w-3/5 mx-auto px-4 md:py-16 py-8 text-center max-w-4xl">
		<h2 class="font-semibold text-2xl">Sponsors</h2>
		<hr class="border-black border-2 rounded-lg w-52 mx-auto" />
		<div class="grid gap-3">
			<ul class="grid grid-cols-1 gap-3">
				{#each sponsors.platinum as sponsor}
					<Sponsor {...sponsor} is_platinum={true} />
				{/each}
			</ul>
			<ul class="grid lg:grid-cols-3 grid-cols-2 gap-3">
				{#each sponsors.gold as sponsor}
					<Sponsor {...sponsor} />
				{/each}
			</ul>
		</div>
		<a
			class="bg-crystal-800 hover:bg-crystal-700 transition-colors px-4 py-3 rounded-lg text-white font-semibold w-full sm:w-56 mx-auto"
			href="/sponsors">Become a sponsor</a
		>
	</div>
</article>
