<script>
	import data from './data';
	import { page } from '$app/stores';

	const style = {
		title: `mx-4 text-sm`,
		section: `font-medium mb-4 pl-5 text-gray-500 text-lg lg:pl-6`,
		link: `flex items-center justify-start my-1 p-3 text-white w-full`,
		active: `border-white lg:border-red-300 border-l-4 lg:border-l-0 lg:border-r-4`
	};
</script>

<ul class="mt-6 md:pl-6">
	<li>
		{#each data as section, i (section.section)}
			<div class="mb-10">
				<div class={style.section}>{section.section}</div>
				{#each section.content as item, i (item.title)}
					<a
						href={item.link}
						class={`${style.link} ${item.link === $page.url.pathname && style.active}`}
					>
						<span><svelte:component this={item.icon} /></span>
						<span class={style.title}>{item.title}</span>
					</a>
				{/each}
			</div>
		{/each}
	</li>
</ul>
