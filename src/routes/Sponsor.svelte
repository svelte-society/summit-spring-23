<script lang="ts">
	import { PUBLIC_API_URL } from '$env/static/public';

	export let name: string;
	export let type: 'platinum' | 'gold';
	export let id: string;
	export let logo: string;
	export let href: string;
	export let is_platinum = false;

	const height = is_platinum ? 100 : 75;
	const fallback = is_platinum ? '💎 Platinum' : '🏆 Gold';
</script>

{#if type}
	<li class="bg-slate-900 p-10 rounded-md text-white gap-3 hover:scale-[1.02] transition-transform">
		<a {href} target="_blank" rel="noreferrer">
			<picture>
				<!-- load webp if supported -->
				<source
					srcset="//wsrv.nl/?url={PUBLIC_API_URL}/files/sponsors/{id}/{logo}&h={height *
						2}&output=webp"
					type="image/webp"
				/>
				<!-- load in case no `source` format applies 
										  and use attributes for presentation -->
				<img
					height="{height}px"
					class="mx-auto"
					src="//wsrv.nl/?url={PUBLIC_API_URL}/files/sponsors/{id}/{logo}&h={height * 2}"
					alt="{name} logo"
				/>
			</picture>
		</a>
	</li>
{:else}
	<li
		class:py-12={is_platinum}
		class="bg-slate-900 rounded-md p-8 text-white gap-3 hover:scale-[1.02] transition-transform"
	>
		<a href="/sponsors">{fallback}</a>
	</li>
{/if}
