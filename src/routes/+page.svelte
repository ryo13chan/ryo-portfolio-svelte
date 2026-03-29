<script lang="ts">
	import { Button } from '$lib/components/ui/button/index.js'
	import Camera from '@lucide/svelte/icons/camera'

	const test = () => alert()
</script>

<Button onclick={test}>Click me</Button>
<Button size="icon">
	<Camera />
</Button>
<h1 class="text-9xl">Welcome to SvelteKit</h1>
<p class="mt-4 text-lg text-gray-600">ポートフォリオサイトへようこそ</p>
