<script lang="ts">
	import { resolve } from '$app/paths'
	import icon from '$lib/assets/icon.jpg'
	import { Avatar, AvatarFallback, AvatarImage } from '$lib/components/ui/avatar'
</script>

<a href={resolve('/')}>
	<Avatar class="h-12 w-auto">
		<AvatarImage src={icon} alt="@shadcn" />
		<AvatarFallback>CN</AvatarFallback>
	</Avatar>
</a>
