<script lang="ts">
	import { resolve } from '$app/paths'
	import Avatar from '$lib/components/feature/avatar/Avatar.svelte'
	import Badge from '$lib/components/ui/badge/badge.svelte'
	import type { CommitData } from '$lib/types/git'
	import GitCommitVertical from '@lucide/svelte/icons/git-commit-vertical'
	import { differenceInDays, format } from 'date-fns'
	import { onMount } from 'svelte'

	onMount(async () => {
		await fetchGitCommitData()
	})

	let gitCommitData = $state<CommitData | null>(null)
	//  1週間以内のcommitか
	const isRecentCommit = $derived.by(() => {
		if (!gitCommitData) return false
		const commitDate = new Date(gitCommitData.commit.author.date)
		const now = new Date()
		return differenceInDays(now, commitDate) <= 7
	})
	const fetchGitCommitData = async () => {
		const getCommitDataResponse = await fetch(
			'https://api.github.com/repos/ryo13chan/ryo-portfolio-svelte/commits/main'
		)
		gitCommitData = await getCommitDataResponse.json()
	}
</script>

<header class="sticky top-0 flex h-20 items-center justify-between border-b bg-white px-4">
	<div class="flex items-center gap-4">
		<Avatar />
		{#if gitCommitData}
			<div class="hidden flex-col gap-1 sm:flex">
				<div class="flex items-center gap-2">
					<span>
						{format(new Date(gitCommitData.commit.author.date), 'yyyy/MM/dd')}
					</span>
					{#if isRecentCommit}
						<Badge>New</Badge>
					{/if}
				</div>
				<div class="flex items-center">
					<GitCommitVertical />
					<a href={gitCommitData.html_url} target="_blank" rel="noreferrer external">
						{gitCommitData.commit.message}
					</a>
				</div>
			</div>
		{/if}
	</div>
	<div class="flex gap-4">
		<!-- eslint-disable-next-line svelte/no-navigation-without-resolve -->
		<a href={`${resolve('/')}#about`}>About</a>
		<!-- <a href={resolve('/works')}>Works</a> -->
	</div>
</header>
