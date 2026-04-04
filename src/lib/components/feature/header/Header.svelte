<script lang="ts">
	import { resolve } from '$app/paths'
	import Avatar from '$lib/components/base/avatar/Avatar.svelte'
</script>

<header class="sticky top-0 flex h-20 items-center justify-between border-b bg-white px-4">
	<div class="flex items-center gap-4">
		<Avatar />
		<!-- TODO: Git履歴コンポーネント -->
	</div>
	<div class="flex gap-4">
		<!-- eslint-disable-next-line svelte/no-navigation-without-resolve -->
		<a href={`${resolve('/')}#about`}>About</a>
		<!-- <a href={resolve('/works')}>Works</a> -->
	</div>
</header>
