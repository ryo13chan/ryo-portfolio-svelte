<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js'
	import Camera from '@lucide/svelte/icons/camera'

	const test = () => alert()
</script>

<div class="flex min-h-screen flex-col items-center justify-center gap-4">
	<h1 class="text-5xl">Welcome to SvelteKit</h1>
	<p class="mt-4 text-lg text-gray-600">ポートフォリオサイトへようこそ</p>
	<Button onclick={test}>Click me</Button>
	<Button size="icon">
		<Camera />
	</Button>
</div>
<div id="about">about</div>
<div class="h-screen"></div>
